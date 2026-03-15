# Architecture of Agency (Agentic Design Patterns): The Market Sentinel 🏗️🧠

A comprehensive guide to 11 essential Agentic AI design patterns, built for clarity, simplicity, and enterprise value.

### SETUP
* **Python Version:** These patterns work best on Python 3.10+ due to the heavy use of type hinting and TypedDict.

* **Visualization:** LangGraph's draw_mermaid_png() usually works out of the box by hitting a web API, but if someone is working offline, they might need to install pygraphviz (which can be tricky on Windows).
---

## 01. The Sequential Pattern (The Assembly Line)

The most fundamental pattern in agentic design. This mimics a traditional industrial assembly line where the output of one agent is the mandatory input for the next.

### Key Concepts:

* **Deterministic Flow:** You know exactly who handles the data next.
* **State Handoffs:** Each node updates a specific part of the shared "State" (Clipboard).
* **Modularity:** You can change how data is fetched without touching how it is analyzed.

---

## 02. The Parallel Pattern (The Fan-Out/Fan-In)

The Parallel pattern is built for speed and multifaceted analysis. Instead of a single line, the workflow branches out to multiple agents who operate independently and simultaneously.

### Key Concepts:

* **Efficiency:** Multiple tasks are performed in the same time-step.
* **Specialization:** Different agents can focus on different data sources (e.g., one for Technicals, one for Fundamentals).
* **Synchronization:** The "Aggregator" node acts as a barrier, waiting for all parallel workers to finish before producing the final result.

---

## 03. The Router Pattern (The Intelligent Gatekeeper)

The Router pattern introduces dynamic decision-making. Instead of every agent running every time, a "Router" node evaluates the input and directs the workflow down the most relevant path.

### Key Concepts:

* **Resource Optimization:** Only trigger the agents that are actually needed for the specific task.
* **Intent Recognition:** The system can handle multiple types of requests (e.g., Support vs. Sales) within a single architecture.
* **Conditional Logic:** Uses "Conditional Edges" to create forks in the workflow based on the current state.

---

## 04. The Coordinator Pattern (The Project Manager)

The Coordinator pattern moves from simple routing to active planning. A central "Manager" node decomposes a high-level user request into a sequence of sub-tasks, which are then executed iteratively.

### Key Concepts:

* **Task Decomposition:** Breaking complex problems into smaller, manageable pieces.
* **Iterative Execution:** Using a feedback loop to process a list of tasks until the goal is met.
* **Dynamic State:** The "Plan" is part of the state and is modified in real-time as tasks are completed.

---

## 05. The Iterative Refinement Pattern (The Progressive Polisher)

The Iterative Refinement pattern introduces a feedback loop where an agent critiques and improves its own work. This ensures that the final output meets a specific quality threshold before it is delivered.

### Key Concepts:

* **Self-Correction:** The system acts as its own editor, identifying and fixing weaknesses in real-time.
* **Exit Conditions:** Essential for production—the loop must break when quality is met or a maximum iteration limit is reached to prevent infinite loops.
* **Incremental Improvement:** Each pass adds more detail, accuracy, or professional tone to the initial draft.

---

## 06. The Evaluator-Optimizer Pattern (The Critic & The Creator)

This pattern formalizes the separation of "doing" and "checking." It uses a generator node (the Optimizer) to produce an output and a specialized checker node (the Evaluator) to validate it against a set of standards.

### Key Concepts:

* **Model Asymmetry:** In production, you can use a smaller model to generate and a more capable model to evaluate, balancing cost and quality.
* **Separation of Concerns:** By isolating the "grading" logic, you reduce the confirmation bias inherent in a single agent reviewing its own work.
* **Deterministic Quality:** The Evaluator acts as a gatekeeper, ensuring no output leaves the system unless it hits a specific score or criteria.

---

## 07. The Swarm Pattern (Decentralized Collaboration)

The Swarm pattern mimics a peer-to-peer network. Agents operate with high autonomy, "handing off" the state to other specialists based on the evolving needs of the task.

### Key Concepts:

* **Fluid Handoffs:** There is no fixed sequence; agents decide who is best suited to handle the next step in the conversation.
* **Shared Context:** All agents contribute to a common "pool" of notes or knowledge, ensuring the final aggregator has a 360-degree view.
* **Dynamic Routing:** Perfect for scenarios where the path to a solution isn't clear at the start.

---

## 08. Hierarchical Pattern (Task Decomposition)

The Hierarchical pattern organizes agents into a top-down structure. A lead "Manager" or "CEO" agent receives the primary goal and decomposes it into sub-tasks for specialized subordinate agents.

### Key Concepts:

* **Abstraction:** The CEO doesn't need to know "how" the research is done; they only care about the final report from the Research Manager.
* **Scalability:** By nesting hierarchies, you can manage incredibly complex workflows that would overwhelm a single agent's context window.
* **Controlled Collaboration:** Information flows through defined channels, preventing the "chaos" that can sometimes occur in flat swarm structures.

---

## 09. The ReAct Pattern (Reason + Act)

The ReAct pattern is the standard for agents that need to interact with the real world. It combines Reasoning (the LLM's ability to plan) with Acting (the ability to use external tools).

### Key Concepts:

* **The Loop:** Instead of a single pass, the agent moves through a Thought -> Action -> Observation cycle until it has enough information to answer.
* **Grounding:** By using tools like search engines or calculators, the agent anchors its responses in real-time data rather than relying solely on its training data.
* **Traceability:** You can see exactly why an agent chose a specific tool by inspecting the "Thought" steps in the state.

---

## 10. The Human-in-the-Loop Pattern (The Mandatory Handshake)

In high-stakes environments, total autonomy is a risk. This pattern introduces a stateful "Pause" in the agent's workflow, requiring a human to validate the plan before the most critical actions are executed.

### Key Concepts:

* **State Serialization:** The agent’s memory is saved to a persistent store (Checkpointing), allowing the system to wait for hours or days without losing context.
* **Interrupts:** Specific nodes are flagged as "Protected," meaning the graph will always stop execution before entering them.
* **Human Verification:** The final decision is anchored in human accountability, providing a legal and ethical paper trail for AI actions.

---

## 11. The Safety Guardrail Pattern (The AI Firewall)

The final layer of enterprise readiness. Guardrails provide a deterministic security layer that sits around the stochastic (unpredictable) nature of LLMs.

### Key Concepts:

* **Pre-Processing (Input):** Prevents "Prompt Injection" and ensures the user stays within the defined scope of the application.
* **Post-Processing (Output):** Uses pattern matching (Regex) or specialized classifiers to detect and redact PII, toxic content, or proprietary data.
* **Fail-Safe Design:** If a guardrail fails, the system is designed to stop or return a generic error message rather than risk a security breach.


