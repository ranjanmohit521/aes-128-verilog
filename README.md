# AES-128 Encryption Hardware

![Verilog](https://img.shields.io/badge/HDL-Verilog-blue)
![AES-128](https://img.shields.io/badge/Cryptography-AES--128-green)
![RTL](https://img.shields.io/badge/Design-RTL-orange)
![Status](https://img.shields.io/badge/Status-In%20Development-yellow)

A Verilog HDL implementation of the Advanced Encryption Standard (AES-128) for hardware-based symmetric encryption.

---

## Overview

This project implements the AES-128 encryption algorithm using Verilog HDL.

AES (Advanced Encryption Standard) is a symmetric-key cryptographic algorithm used for secure data encryption. AES-128 operates on a 128-bit data block using a 128-bit encryption key and performs 10 transformation rounds.

The project explores the implementation of cryptographic operations at the RTL hardware level, including byte substitution, row shifting, column mixing, round-key generation, and XOR-based key addition.

---

## AES-128 Specifications

| Parameter | Specification |
|---|---|
| Algorithm | Advanced Encryption Standard |
| Variant | AES-128 |
| Block Size | 128 bits |
| Key Size | 128 bits |
| Number of Rounds | 10 |
| Input | 128-bit Plaintext |
| Output | 128-bit Ciphertext |
| HDL | Verilog |
| Design Level | RTL |

---

## Architecture

```text
                    128-bit Encryption Key
                              |
                              v
                    +-------------------+
                    |   Key Expansion   |
                    +---------+---------+
                              |
                    Round Keys 0 - 10
                              |
                              |
+-------------------+         |
| 128-bit Plaintext |         |
+---------+---------+         |
          |                   |
          v                   |
   +--------------+           |
   | AddRoundKey  |<----------+
   +------+-------+
          |
          v
   +----------------------+
   |      AES Rounds      |
   |                      |
   |     SubBytes         |
   |         |            |
   |     ShiftRows        |
   |         |            |
   |     MixColumns       |
   |         |            |
   |     AddRoundKey      |
   +----------+-----------+
              |
              v
       +--------------+
       | Final Round  |
       |              |
       |  SubBytes    |
       |  ShiftRows   |
       |  AddRoundKey |
       +------+-------+
              |
              v
    +---------------------+
    | 128-bit Ciphertext  |
    +---------------------+
