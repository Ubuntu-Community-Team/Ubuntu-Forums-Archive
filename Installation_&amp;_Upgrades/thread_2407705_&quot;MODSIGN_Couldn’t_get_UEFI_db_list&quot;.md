---
title: "&quot;MODSIGN: Couldn’t get UEFI db list&quot;"
date: 2018-12-07
forum: Installation &amp; Upgrades
---

### Post by jabrilm on 2018-12-07
I'm encountering the error "MODSIGN: Couldn’t get UEFI db list" when trying to install Ubuntu 18.10, and a web search reveals Secure Boot as the likely culprit. However, Secure Boot has already been disabled in BIOS. What are other possible sources of this error?

Trying to install from a USB stick on an HP Spectre x360 laptop. Aiming for a dual-boot Ubuntu OS alongside Windows 10.

---

### Post by oldfred on 2018-12-07
This user changed a UEFI setting.
       Change UEFI settings from custom to standard
[https://ubuntuforums.org/showthread.php?t=2380700](https://ubuntuforums.org/showthread.php?t=2380700)

---

### Post by jabrilm on 2018-12-07
Thanks. But my BIOS does not give that option for UEFI. 

After trying a lot of things, I was able to get past the error in the OP by adding the grub arguments [FONT=courier new]noapic noacpi nosplash[/FONT] in place of [FONT=courier new]quiet splash[/FONT].

---

### Post by c1onado on 2019-01-18
> **jabrilm said:**
> Thanks. But my BIOS does not give that option for UEFI. 

After trying a lot of things, I was able to get past the error in the OP by adding the grub arguments [FONT=courier new]noapic noacpi nosplash[/FONT] in place of [FONT=courier new]quiet splash[/FONT].


Thank's a lot, you just saved my life.

---

