# The 5 Qubit Stabiliser Code

## Description

This project implements the 5-qubit quantum error correction code using Qiskit. The code encodes one logical qubit across five physical qubits to protect against any single-qubit error, including bit flips (\(X\)), phase flips (\(Z\)), or their combination (\(XZ\)). Stabilization is achieved through four stabilizer operators, and syndrome measurements identify and locate errors. The implementation includes encoding, an example error, stabilizer measurements, and simulation.

## Code Structure

The main script constructs a quantum circuit with the following steps:

1. **Encoding**: The logical qubit on `q0` is encoded into a 5-qubit state using Hadamard (`H`), Pauli-\(Z\) (`Z`), CNOT (`CX`), and controlled-\(Z\) (`CZ`) gates. The resulting state aligns with the 5-qubit code’s properties (see [Wikipedia: Five-qubit error correcting code](https://en.wikipedia.org/wiki/Five-qubit_error_correcting_code)). A commented section allows verification of the statevector.

2. **Error Injection**: A single \(Z\) error is applied to `q2` as an example. This can be modified to test other error types.

3. **Stabilizer Measurement**: Four ancilla qubits measure the stabilizers:
   - \(S1 = XZZXI\)
   - \(S2 = IXZZX\)
   - \(S3 = XIXZZ\)
   - \(S4 = ZXIXZ\)
   Each stabilizer is implemented with Hadamard and controlled gates, followed by measurement into a syndrome register.

4. **Simulation**: The circuit is simulated using `AerSimulator` to obtain syndrome outcomes.

## Circuit Diagram

The full circuit, including encoding, error, and stabilizer measurements, is saved as:

<p align="center">
  <img src="531css.png" width="700"/>
</p>

## Requirements

- Qiskit (`qiskit`, `qiskit_aer`)
- Matplotlib (for circuit drawing)

Install with:
```bash
pip install qiskit qiskit-aer matplotlib
