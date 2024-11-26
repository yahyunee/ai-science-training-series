## Key Architectural Features for AI Workloads

AI accelerator systems, including **Cerebras**, **Graphcore**, **SambaNova**, and **Groq**, are designed with distinct architectural innovations to address the demands of modern AI workloads. Key features include:

1. **Massive Parallelism**:
   - **Cerebras**: The **Wafer-Scale Engine (WSE)** provides hundreds of thousands of cores for extreme parallelism, particularly beneficial for large deep learning models.
   - **Graphcore**: Uses **Intelligence Processing Units (IPUs)** designed for fine-grained parallelism and low-latency execution of graph-based AI computations.
   - **SambaNova**: Leverages **Reconfigurable Dataflow Units (RDUs)** for dynamically optimized parallel computation.
   - **Groq**: Implements a **Tensor Streaming Processor (TSP)** architecture, enabling deterministic execution and efficient parallelization.

2. **High Memory Bandwidth and On-Chip Storage**:
   - **Cerebras**: Features distributed on-chip SRAM near the cores, minimizing data movement.
   - **Graphcore**: Includes tightly coupled memory and processors, with fast access for high-performance matrix operations.
   - **SambaNova**: Offers reconfigurable memory to optimize specific AI model requirements.
   - **Groq**: Provides high-bandwidth memory to sustain tensor streaming without bottlenecks.

3. **Scalability**:
   - These accelerators are designed for seamless scalability, supporting multi-device configurations for training or inference of large AI models.

4. **Flexibility and Specialization**:
   - **Graphcore**: Optimized for graph-centric machine learning and non-standard models.
   - **SambaNova**: Tailored for a wide range of workloads, including NLP, computer vision, and recommendation systems.
   - **Groq**: Excels in deterministic and real-time workloads.
   - **Cerebras**: Focuses on massive, dense computation for large-scale AI workloads.

---

## Primary Architectural and Programming Model Differences

| Feature                     | Cerebras                                                                                 | Graphcore                                                                                 | SambaNova                                                                                 | Groq                                                                                     |
|-----------------------------|------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| **Core Architecture**       | Wafer-Scale Engine (WSE)                                                                 | Intelligence Processing Unit (IPU)                                                       | Reconfigurable Dataflow Units (RDU)                                                      | Tensor Streaming Processor (TSP)                                                        |
| **Memory Design**           | Distributed SRAM close to processing cores                                               | Tightly coupled in-processor memory                                                      | Reconfigurable memory hierarchy                                                          | High-bandwidth memory                                                                    |
| **Optimization Target**     | Extreme acceleration of large models (e.g., GPT, BERT)                                   | Graph-based computations and workloads requiring fine-grained parallelism                | General-purpose AI, flexible across NLP, CV, and recommendation systems                 | Deterministic workloads requiring precision and efficiency                               |
| **Programming Model**       | Supports TensorFlow, models require optimization for chip-scale architecture             | Poplar SDK integrates with TensorFlow, PyTorch                                           | Dataflow graph compilation, integrates with PyTorch and TensorFlow                       | GroqFlow SDK supports TensorFlow and PyTorch                                            |
| **Specialized Features**    | Wafer-scale chip eliminates interconnect bottlenecks                                     | Strong support for sparsity and non-standard computational graphs                        | Versatile reconfigurability for custom AI pipelines                                      | Deterministic execution for latency-critical applications                                |

---

## Workflow for Refactoring AI Models to Run on ALCF AI Testbeds

1. **Evaluate Suitability**:
   - Match the model’s architecture and workload with the strengths of the target system:
     - Use **Cerebras** for large dense models.
     - Use **Graphcore** for sparse and graph-based models.
     - Use **SambaNova** for versatility across tasks.
     - Use **Groq** for deterministic and latency-sensitive tasks.

2. **Prepare the Model**:
   - Refactor the AI model using the respective SDKs:
     - **Cerebras**: Optimize memory usage and adjust layers to fit the WSE.
     - **Graphcore**: Leverage the Poplar SDK to define computational graphs.
     - **SambaNova**: Rewrite using the Dataflow SDK for optimized performance.
     - **Groq**: Adapt code to the GroqFlow SDK for efficient tensor streaming.

3. **Benchmark and Profile**:
   - Use provided profiling tools to analyze the performance:
     - **Cerebras**: On-chip profiling tools to monitor core utilization.
     - **Graphcore**: Use Graph Analyzers in the Poplar SDK.
     - **SambaNova**: Measure dataflow efficiency using integrated diagnostics.
     - **Groq**: Profiling for latency and deterministic behavior.

4. **Iterate and Optimize**:
   - Refine model partitioning, hyperparameters, or layer configurations based on feedback from the profiling tools.

5. **Deploy and Validate**:
   - Deploy the refactored model on the AI testbed, verify accuracy, and evaluate performance.

---

## Example Project Benefiting from AI Accelerators

#### **Project: Drug Discovery Using Molecular Graph Neural Networks**

- **Why it Benefits**:
  - **Graphcore (IPUs)**: Ideal for processing molecular graphs due to fine-grained parallelism and support for graph neural networks (GNNs).
  - **Cerebras (WSE)**: Provides computational power to train large-scale GNNs rapidly.
  - **SambaNova (RDUs)**: Flexible architecture handles diverse inputs from chemical datasets.
  - **Groq (TSP)**: Ensures deterministic and efficient simulation of molecular dynamics.

This project requires parallel computation, rapid iteration, and large-scale model training—features perfectly aligned with AI accelerator capabilities.
