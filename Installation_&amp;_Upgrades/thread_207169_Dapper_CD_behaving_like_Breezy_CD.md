---
title: "Dapper CD behaving like Breezy CD"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by Luke771 on 2006-07-01
System: AMD Duron 1600 - 512RAM - hda Matrox 40g - hdb matrox 80g - video nVidia GeForce4 64MB - Ethernet VIA 10mb/s - connection: fiber 10mb/s behind ISP NAT.

**Short story:** The first time I installed Dapper it run from a Live CD but on clean reinstall the same CD on the same machine run a text-based install. How is that possible?

**Long story**: My system was getting messy so I decided to clean install both Windows and Linux (Dapper): I have two HDDs, hdb is one big ext2 partition used for file storage (running ext2 drivers on Windows) and hda holds the OSes (WinXP on hda1 and Dapper on hda2).

**When I  first clean installed Dapper, the install CD behaved like a live CD** and loaded a Gnome desktop with a couple of icons on it, one of them being called "Install": All I had to do was double click that icon to get to a nice graphical installer that I could run and let it copy and configure stuff while I was surfing the web at the same time.

OK: I decided to clean install both OSes so I run Partition Magic and deleted all partitions on hda leaving hdb alone because my files were on it.

After deleting everything from hda, I created a NTFS  primary hda1 for Windows, a Ext2 primary hda2, one logical swap space and a couple of partitions not to be used on Linux (dedicated gaming part and page file dedic. par.)

I installed Windows on hda1 first and then I booted from *the same* Dapper install CD I used last time.

**This time, it didn't run any live Ubuntu: it run a text-based installation program, just like the Breezy CD used to do.**

The installation went fine and everithing is working so far, but I just don't get it: How can the same CD on the same machine run a Live Ubuntu the first time and a text-based install the second time?

---

