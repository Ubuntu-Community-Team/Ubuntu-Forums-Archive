---
title: "Installing an encrypted /, /home and swap while preserving existing partitions"
date: 2020-07-30
forum: Installation &amp; Upgrades
---

### Post by Gijsbert_Wiesenekk on 2020-07-30
Hi,

Following up on the closed thread with the same title: I upgraded to Ubuntu 20.04 but switched to EFI. The instructions are largely the same with the following modifications:

I did not have free partition space for the EFI partition, so:

Delete the existing /boot partition. My /boot partition size was 1024MB.
Create an EMPTY partition for EFI in the freed up space using gparted. I used 128MB for the size which appears to be sufficient for Ubuntu. Do NOT create it as an EFI partition, the installation will fail (this seems to be a common issue). The workaround is to have the installer create the EFI partition.
Create an ext2 /boot partition in the remaining freed up space using gparted.

Follow the instructions in the closed thread with the same title.

Regards,
GW

---

### Post by TheFu on 2020-07-30
what closed thread?

---

