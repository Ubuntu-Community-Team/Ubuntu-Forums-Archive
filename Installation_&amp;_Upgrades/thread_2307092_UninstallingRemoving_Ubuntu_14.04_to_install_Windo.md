---
title: "Uninstalling/Removing Ubuntu 14.04 to install Windows 7"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by Tyler_Rau on 2015-12-21
So, I do not have GRUB installed, as I run Ubuntu 14.04 solo (I am not dual booting, no other OS is installed) and every guide/thread/posting I've come across on how to reformat the drive from its current (Ubuntu uses FAT or something or another) formatting to one that can be used to install Windows 7 (NTSF, if I'm not mistaken), always has someone who is dual booting both Windows and Ubuntu.

My question is: How do I reformat my hard drive so that I can do a clean install of Windows 7 or, if this is not a viable option, how can I go about getting from Ubuntu 14.04 to Windows 7. I plan on Installing Windows off of a disk. 

I don't know what other information you guys would need, so just let me know and I'll fill you in on everything as best as I can.

---

### Post by QIII on 2015-12-21
You do have GRUB installed.  You just don't ever see it.

Personally, I'd use a live DVD/USB and run Gparted to delete all the partitions and create one large NTFS partition and simply install Windows. 

The Windows installer should just be able to reformat the drive, but It doesn't hurt to make sure it doesn't get confused.

Was this a UEFI or BIOS installation of Ubuntu?

---

### Post by mrroberthadley on 2015-12-21
You would need to either 1, resize your HDD and create another partition or 2, just boot form the windows disk and reformat the whole drive and install windows.

---

### Post by Bucky Ball on 2015-12-21
Boot from a Windows disk, gives you the option to delete partitions, then install Windows. It will kill anything.

The important bit, though, is QIII's question regarding a UEFI or BIOS boot.

---

### Post by Bucky Ball on 2015-12-22
In that case, boot from the Win disk, delete all partitions, install Windows.

---

