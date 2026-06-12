---
title: "Problem Installing Ubuntu on Sata HDD"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by shimabuku on 2008-11-10
Hello, I am new to linux/ubuntu. I am trying to install ubuntu 8.10 desktop amd64 on my PC but for some reason it is not detecting my Sata hdd. The BIOS sees both the sata hdd and ide hdd just fine. Here is my desktop build.

A8N32-SLI Deluxe / Bios Ver. 1303
AMD64 3800+
WD SATA II 250GB
Seagate IDE 120GB
PNY 6600GT PCI-E
2GB DDR400

I have tried the "acpi=off noapic" options at the boot command. Also, there is no drive setting in the BIOS to set it to AHCI. I have not tried the AlternateCD yet as i am new to this linux thing. Any help would be greatly appreciated.

---

### Post by shimabuku on 2008-11-10
Anyone?

---

### Post by Pumalite on 2008-11-10
Check Dualboot 2 Hard Drives:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by jimbudler on 2008-11-11
> **shimabuku said:**
> Hello, I am new to linux/ubuntu. I am trying to install ubuntu 8.10 desktop amd64 on my PC but for some reason it is not detecting my Sata hdd. The BIOS sees both the sata hdd and ide hdd just fine. Here is my desktop build.

A8N32-SLI Deluxe / Bios Ver. 1303
AMD64 3800+
WD SATA II 250GB
Seagate IDE 120GB
PNY 6600GT PCI-E
2GB DDR400

I have tried the "acpi=off noapic" options at the boot command. Also, there is no drive setting in the BIOS to set it to AHCI. I have not tried the AlternateCD yet as i am new to this linux thing. Any help would be greatly appreciated.

I had to add rootdelay=60 to the kopt in menu.lst . It would boot just fine with the 2.6.24 kernel. I edit this, below and ran update-grub

# kopt=root=UUID=4aaa520a-79dc-499f-80f8-6955bbaf4833 ro
# kopt_2_6_27=root=UUID=4aaa520a-79dc-499f-80f8-6955bbaf4833 ro rootdelay=60

---

