---
title: "How to access TPM FDE data?"
date: 2024-09-13
forum: Installation &amp; Upgrades
---

### Post by Blaimi on 2024-09-13
Hi,

I installed successfully a new 24.04 system with the experimental encryption option with using a TPM for full disk encryption (FDE). I have the recovery key extracted with ```
sudo snap recovery --show-keys
```. Now imagine, that e.g. my mainboard dies because of reasons or the bootloader gets corrupted.

**How can I access the data by disassembling my device and putting the drive into another system or from a live-system?**

I cannot find anything on that topic online. I know there are files in `/run/mnt/ubuntu-seed/device/fde` on the EFI partition, but I don't know how I can use them. I assume, that these files get somehow decrypted with the key saved in the TMP and used as keyfile for the devices `ubuntu-save` and `ubuntu-data` but how can I decrypt them when I don't have a TPM but only the recovery-key?

If I can't find a solution for this, using ubuntus FDE with TPM is absolutely not usable for me. I mean, I have backups of everything if my disk dies but I had way more defects on other parts of my system than on the disk. And bringing back a system from backups is always a lot more work than c&p data from one disk to another.

Thanks in advance
Blaimi

---

### Post by Blaimi on 2024-09-26
found the solution: [https://github.com/jps-help/python-snap2luks/issues/2#issue-2551650039](https://github.com/jps-help/python-snap2luks/issues/2#issue-2551650039)

---

