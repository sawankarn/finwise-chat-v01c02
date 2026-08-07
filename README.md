# 📗 Volume 1 · Chapter 2: Talking to Intelligence: Prompts & Models

# FinWise Chat

> **Edition B — NextGen Visual Edition**
> _Story-driven · Illustration-rich · Production-oriented_

Welcome to the second chapter of the FinWise AI Engineering Academy! This module builds upon our basic chat interface by introducing system prompts (personas), streaming responses, and PromptTemplates for more dynamic and professional interactions.

---

## 📝 Chapter Summary

In this chapter, we explore how to effectively communicate with Large Language Models by treating prompts as contracts. We learn how to define system personas, implement streaming responses to improve user experience, and structure our prompts using Spring AI's PromptTemplate for dynamic, context-aware interactions.

---

## 📖 Chapter Learning Objectives

- [ ] Understand the concept of prompt as a contract
- [ ] Define system personas to guide LLM behavior
- [ ] Implement streaming for a better user experience
- [ ] Use `PromptTemplate` for dynamic prompt generation

---

## 🚀 Features

- **Spring AI Integration**: Uses the stable `1.0.0` release.
- **System Prompts**: Configured to act strictly as a FinWise financial advisor.
- **Streaming Responses**: Delivers faster, token-by-token responses to improve UX.
- **PromptTemplates**: Dynamic context injection using variables.
- **Gemini Powered**: Configured out of the box to use Google's `gemini-2.5-flash` model.
- **Local Fallback**: Includes an `application-local.yml` profile for running offline with Ollama.
- **Java 25 Ready**: Pre-configured to build with JDK 21 (Loom EA).

---

## 📁 Folder Structure

```text
chapter2/
├── ch02_chapter2.md             ← Full chapter content (NextGen Visual format)
├── ch02_quiz.md                 ← Chapter quiz with answers
├── ch02_mission.md              ← Hands-on mission card
└── finwise-chat-v01c02/         ← Working Spring Boot project
    ├── README.md                ← You are here
    ├── pom.xml
    └── src/
        ├── main/
        │   ├── java/com/finwise/
        │   │   ├── FinwiseChatApplication.java
        │   │   ├── chat/
        │   │   │   ├── ChatService.java
        │   │   │   └── ChatController.java
        │   │   └── config/
        │   │       └── AiConfig.java
        │   └── resources/
        │       ├── application.yml
        │       └── application-local.yml
        └── test/
            └── java/com/finwise/chat/
                └── ChatServiceTest.java
```

---

## 🛠️ Prerequisites

1. **JDK 21**: Make sure you have JDK 21 installed.
2. **Gemini API Key**: Get a free API key from [Google AI Studio](https://aistudio.google.com/).

---

## 💻 How to Run

### Option A: Using Command Prompt (`cmd.exe`)

Open your command prompt, navigate to this directory, and run the following commands:

```cmd
:: 1. Point to your JDK 21 installation
set JAVA_HOME=C:\path\to\your\jdk-21

:: 2. Set your Gemini API key
set GEMINI_API_KEY=your_actual_key_here

:: 3. Run the application
.\mvnw.cmd clean install
.\mvnw.cmd spring-boot:run
```

### Option B: Using PowerShell

Open PowerShell, navigate to this directory, and run:

```powershell
# 1. Point to your JDK 21 installation
$env:JAVA_HOME="C:\path\to\your\jdk-21"

# 2. Set your Gemini API key
$env:GEMINI_API_KEY="your_actual_key_here"

# 3. Run the application
.\mvnw clean install
.\mvnw spring-boot:run
```

### Option C: Using macOS/Linux Bash

```bash
# 1. Set your Gemini API key
export GEMINI_API_KEY=your_actual_key_here

# 2. Run the application
./mvnw clean install
./mvnw spring-boot:run
```

### Option D: Using IntelliJ IDEA

1. Open this project in IntelliJ.
2. Go to **File -> Project Structure** and ensure the Project SDK is set to your JDK 21.
3. Edit your Run Configuration for `FinwiseChatApplication`:
   - Under **Environment variables**, add: `GEMINI_API_KEY=your_actual_key_here`
4. Click **Run**.

---

## 🧪 Testing the Application (Supported Examples)

Once the application starts successfully (usually on port 8080), you can test the REST endpoints. The application exposes two main endpoints:

### 1. Send a Chat Message (`POST /api/chat`)

This is the main endpoint to interact with the financial advisor AI.

**Using curl (Command Prompt / Git Bash):**

```bash
curl -X POST http://localhost:8080/api/chat \
  -H "Content-Type: application/json" \
  -d "{\"message\": \"What is compound interest?\", \"sessionId\": \"user-123\"}"
```

**Expected Response:**

```json
{
  "reply": "Compound interest is the interest you earn on both your original money and on the interest you keep accumulating...",
  "sessionId": "user-123",
  "model": "gemini-2.5-flash"
}
```

### 2. Check AI Health (`GET /api/chat/health`)

This endpoint verifies that the LLM provider (Gemini or Ollama) is reachable and responding.

**Using your Web Browser:**
Simply navigate to: [http://localhost:8080/api/chat/health](http://localhost:8080/api/chat/health)

**Using curl:**

```bash
curl http://localhost:8080/api/chat/health
```

**Expected Response:**

```json
{
  "status": "ok",
  "provider": "gemini-2.5-flash",
  "latencyMs": 432
}
```

### 3. Stream a Chat Message (`POST /api/chat/stream`)

This endpoint streams the AI's response token-by-token.

**Using curl:**

```bash
curl -X POST http://localhost:8080/api/chat/stream \
  -H "Content-Type: application/json" \
  -d "{\"message\": \"What is an ISA?\"}"
```

---

## 🦙 Running Locally with Ollama (Offline)

If you don't want to use Gemini or don't have internet access, you can run the application entirely on your local machine using Ollama:

1. Install [Ollama](https://ollama.com/) and run a local model (e.g., `ollama run llama3`).
2. Run the Spring Boot application with the `local` profile activated:

   **Command Prompt:**

   ```cmd
   .\mvnw.cmd clean install
   .\mvnw.cmd spring-boot:run -Dspring-boot.run.profiles=local
   ```

   **PowerShell:**

   ```powershell
   .\mvnw clean install
   .\mvnw spring-boot:run "-Dspring-boot.run.profiles=local"
   ```

   **Bash:**

   ```bash
   ./mvnw clean install
   ./mvnw spring-boot:run -Dspring-boot.run.profiles=local
   ```

---

## 🔗 Resources

| Resource          | Link                                               |
| ----------------- | -------------------------------------------------- |
| Spring AI Docs    | https://docs.spring.io/spring-ai/reference/        |
| Spring Initializr | https://start.spring.io                            |
| Ollama            | https://ollama.ai                                  |
| Book GitHub       | https://github.com/finwise-academy/volume1-starter |

---

## Next Chapter

Continue your journey with the next project in the series:

| | Details |
|---|---|
| **Chapter**    | Chapter 3: Making Sense of Intelligence - Output and Evaluation |
| **GitHub**     | [https://github.com/sawankarn/finwise-chat-v01c03](https://github.com/sawankarn/finwise-chat-v01c03) |
| **Repository** | finwise-chat-v01c03 |

Clone and get started:

    git clone https://github.com/sawankarn/finwise-chat-v01c03.git
    cd finwise-chat-v01c03

> Keep building - each chapter unlocks new AI superpowers for your FinWise app!