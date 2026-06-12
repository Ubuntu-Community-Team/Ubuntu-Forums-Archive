---
title: "Silicon Image 0680 IDE-Controller"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by Legnad on 2010-03-12
Hello everybody,

I am new to linux systems and excuse myself if this is noobish.

I'm setting up a ubuntu 9.10 server system for the first time now, but I have some problems with the IDE-Controller installed in my system.
The system detects the controller (*lspci*):

```
00:0e.0 RAID bus controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)

```

Somehow the two hard drives connected to the controller are not detected. I have also a SATA-Controller installed and it detects the hard drives connected successfully.

I installed the Storage Device Manager (I added kubuntu), but the hard drives are not listed. I don't know what to do now, any suggestions?

**I have to add, that the system worked with Windows Server 2003 before.**

Thanks in advance for reading and for answering ;)


Greetings

Legnad

EDIT1: I forgot to tell, that all hard drives are not in RAID.

---

