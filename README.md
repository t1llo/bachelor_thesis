# Bachelor Thesis: LLM-Based Code Assistant for IoT Payload Decoders

My bachelor thesis at HSLU (BSc Business Information Technology, 2026), written with [Akenza](https://akenza.io/).

[Bachelor_Thesis.pdf](Bachelor_Thesis.pdf)

## What it's about

IoT sensors send their data as compact, vendor-specific payloads. Before a platform like Akenza can use that data, someone has to write a decoder for every device type: a JavaScript script, JSON schemas, unit tests and a metadata file. That usually takes a developer a few hours per device.

I built an assistant that generates all of these files. It runs several agents one after another (Python, Google ADK, Gemini), each responsible for one part, and is used through a small CLI.

The harder part was measuring whether it actually got better. A decoder can be correct in many different ways, so normal unit tests weren't useful. I wrote a benchmark that checks syntax and rules on the AST, runs the generated decoder in a sandbox against real payloads, and uses an LLM as a judge for the semantic part.

## Results

- One round of improvements based on the benchmark raised the score from 65% to 81%.
- In a timed comparison, creating a decoder took 100 minutes instead of 202.
- Akenza uses it in production, including a customer project where six device types were created in one day.

The test set has only five devices and the time comparison was done with one developer, so take the numbers as a first indication. Sections 6.1 and 6.3 go into this.

The code belongs to Akenza and isn't public, so this repo only contains the thesis.
