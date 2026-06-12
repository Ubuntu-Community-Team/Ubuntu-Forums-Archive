---
title: "Unable to find disk drive when booting"
date: 2022-07-13
forum: Installation &amp; Upgrades
---

### Post by byrnejb on 2022-07-13
I installed ubuntu-22.04-desktop-amd64 on a six year-old laptop that previously had FreeBSD-13.1 installed.  The installation took the default path and completed without error.  However, on the first reboot these messages were observed:  (I am writing this from hand-written notes so some bits and pieces are missing.)

[FONT=Courier New]
[    1.002103] DMAR: failed to find handle for ACPI object \_SB.PCI.SDMA
[    1.002116] DMAR: failed to find handel for ACPI object \_SB.PCI.SDMC

ALERT! /dev/sda does not exist dropping to shell

[initramfs] ls -l /dev/sd*
brw------    1   8,  3  /dev/sda3
brw------    1   8,  2  /dev/sda2
brw------    1   8,  1  /dev/sda1
brw------    1   8,  0  /dev/sda

[initramfs] cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-5.15.0-41-generic root=/dev/sda3  ro  quiet  splash vt.handoff=7
[/FONT]

I had no trouble installing FreeBSD on this device.  What is the probable cause of this issue?

---

