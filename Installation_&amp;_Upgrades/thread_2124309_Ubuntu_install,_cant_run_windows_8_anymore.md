---
title: "Ubuntu install, cant run windows 8 anymore"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by chaot1coz on 2013-03-10
Hello there, today i installed ubuntu 12.10.  i had windows 8 installed already before.. now i  can start ubuntu but not windows 8... so iran boot-repair.. gave me the following:   [http://paste.ubuntu.com/5602708/](http://paste.ubuntu.com/5602708/)
WIndows still doesnt run,, i get errors like no such device and file not found,., can you help me please?

---

### Post by arpanaut on 2013-03-10
[h=4]Windows installer is not compatible with Windows 8 or UEFI firmware[/h]

From:  [http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

You will have to do a full install from the 64 bit Ubuntu desktop iso

---

### Post by chaot1coz on 2013-03-10
this is what i did, i downloaded the x64 iso and installed it from a DVD 5223-61E2

---

### Post by oldfred on 2013-03-10
You have a UEFI install in sda using gpt partitioning.

You have Windows & Linux in sdb with MBR(msdos) partitioning.
You also show a wubi install in sdb.

Wubi does not work from gpt drives.
Windows only boots from gpt drives with UEFI.
Windows 8 pre-installed has secure UEFI boot on a gpt drive.
Ubuntu will boot from gpt partitioned drives with either BIOS or UEFI.

If you boot from UEFI and choose the Windows efi entry does it not boot. You have to have legacy/BIOS/CSM mode off so it does not try to boot in BIOS mode. 
  UEFI Compatibility Support Module (CSM)

It looks like Boot-Repair tried to install grub-efi to boot the install in the MBR drive. Up until a few minutes ago I thought that did not work, but another thread says it works.

---

### Post by arpanaut on 2013-03-10
Did you boot from the dvd, or did you execute it from within windows?
In the pastebin it shows wubi in some places so it looks like a wubi install,
but now I see the linux partitions on sdb...

I'm not familiar with uefi to help with that, hope someone who does comes along.

---

### Post by chaot1coz on 2013-03-10
i did a wubi installiert before then i read it wohnt work with wubi so i installed again Form dvd

---

### Post by oldfred on 2013-03-10
Wubi does work with Windows 8 that you have installed yourself in MBR(msdos) partitioning. 

The issue is wubi does not work with gpt partitioning and Windows 8 pre-installed is UEFI which has to have gpt partitioning.

But if you want to easily dual boot you have to have both system installed in UEFI mode or both in BIOS mode. That usually means both drives should be gpt partitioned.

---

