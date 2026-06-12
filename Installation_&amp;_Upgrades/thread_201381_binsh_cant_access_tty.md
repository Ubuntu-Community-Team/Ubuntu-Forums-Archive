---
title: "bin/sh: cant access tty"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by N!zzo on 2006-06-21
when installation starts I add "irpoll" to boot options to get past 
"uncompressing linux...booting kernel"

but then I get this message 3 seconds later
"/bin/sh: cant access tty - job controll turned off"

could this be because of an irq conflect (nic, audio and usb on same irq)?

also when trying to install ubuntu 6.06 alternate cd it won't install on detect and mount with the message 
"no common cdrom driver was detected"
(tried booting in expert mode but wont give me more options)

could these be related, and is there a solution to this?

---

### Post by N!zzo on 2006-06-21
btw, system specs

asus P5LD2 mobo
Intel Pentium D
DDR2 Ram 2Gb
Nvidia 7600 GS
WD 160 hdd SATA (shared with xp)
BenQ DVD-RW IDE
Sony DVD-ROM IDE

---

### Post by lionelxp on 2007-03-03
linux all-generic-ide pci=nommconf


tis line worked. In the bios change ur SATA to AHCI

---

### Post by ziofester on 2007-06-15
> **lionelxp said:**
> linux all-generic-ide pci=nommconf


tis line worked. In the bios change ur SATA to AHCI


Hi (sorry for my english)

i'have the same problem but i don't have sata drive. I have only a ide hd maxtor 250gb.

have a solution?

tnk
ZioFesTer

---

