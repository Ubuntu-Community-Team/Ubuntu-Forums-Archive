---
title: "When Update Manager updates the kernel, can it automatically run a script?"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by dakra137 on 2010-03-13
Scenario: Ubuntu 9.10 + dazukofs 3.1.2 (required for antivirus)

Example: When Update manager updates the kernel, can I make it recompile and reinstall dazukofs?

Problem:

After Update Manager updates the kernel, say from 2.6.31-17 to 2.6.31-19, and later 2.6.31-20,the new linux won't boot, except in recovery mode. The hang is with the initial ubuntu graphic on the screen.
When going from -17 to -19, grub let me boot normal -17 . After the update to -20, even -17 would hang.

Circumvention:

1) Boot the updated kernel in recovery mode.
2) Change to the dazukofs directory
3) Recompile and install dazukofs
    make
    make dazukofs_install
    modprobe dazukofs

How do I make that happen automatically when needed, whether as part of Update Manager running or as part of the first boot with the updated kernel?

---

