# E91 Quantum Cryptography

A Qiskit simulation of E91 (Ekert, 1991), a quantum cryptography protocol for sharing a secret encryption key. 
The scenario is: Alice and Bob use entangled qubit pairs to build the key, then use a Bell test to check that nobody intercepted it.

## How it works

- **Key:** each round, Alice and Bob measure their halves of an entangled pair at randomly chosen angles. They publicly compare angles, but they never disclose the results, those stay private. Rounds where the angles match give identical bits, which become the key.
- **Spy check:** the other rounds are used to compute a Bell test score, S. Non-entangled systems can reach at most 2 (the CHSH inequality). Entangled pairs reach about 2.83. An eavesdropper has to measure the qubits, which breaks the entanglement and drops S to 2 or below.

## Results

10,000 rounds per run and the numbers vary slightly between runs

| | Key error rate | S |
|---|---|---|
| No eavesdropper | 0% | ~2.83 |
| Eve intercepting | ~20% | ~1.4 |

## Run it

Open in Colab and run all cells, or locally:

```bash
pip install qiskit qiskit-aer matplotlib jupyter
jupyter notebook e91_key_distribution.ipynb
```

## Notes

- E91 secures how the key is shared. Messages are then encrypted normally with that key.
- Real systems use entangled photons over noisy channels, so they tolerate some error.
- This is a simplified simulation for learning.

Made by Sultana with [Qiskit](https://www.ibm.com/quantum/qiskit).
