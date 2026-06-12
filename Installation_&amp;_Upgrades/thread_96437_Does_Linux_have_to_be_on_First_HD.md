---
title: "Does Linux have to be on First HD?"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by CaptainCrunch on 2005-11-28
I have an 80GB Drive in Primary Master and 60GB Drive in Primary Slave.

I currently have Windows XP on 80GB Drive.   The 60GB is empty, unpartitioned.

Must I have a /boot Partition on Master?  Or can I just load Grub in MBR and it will redirect to /boot on Slave?

I'm sorta newbish, so be gentle...   :p

---

### Post by aysiu on 2005-11-28
[QUOTE=CaptainCrunch]I have an 80GB Drive in Primary Master and 60GB Drive in Primary Slave.

I currently have Windows XP on 80GB Drive.   The 60GB is empty, unpartitioned.

Must I have a /boot Partition on Master?  Or can I just load Grub in MBR and it will redirect to /boot on Slave?

I'm sorta newbish, so be gentle...   :p[/QUOTE] You don't need a /boot partition at all. Just install / onto the 60 GB drive and Grub to the MBR.

---

### Post by CaptainCrunch on 2005-11-28
[QUOTE=aysiu]You don't need a /boot partition at all. Just install / onto the 60 GB drive and Grub to the MBR.[/QUOTE]

Thanks.   I tried to convert to Linux a while back.   I thought you had to have Linux Boot Info below a certain cylinder on the Primary Master.    Guess they worked around that.

I guess I'll be installing Ubuntu tomorrow evening.

Thanks again.

---

### Post by taurus on 2005-11-28
You are talking about the 1024 thing!  That is ancient news.  Now, you can put linux anywhere you want to and GRUB should be able to boot it and windows if you still have windows on your machine...

---

### Post by aysiu on 2005-11-28
You know, I've been thinking about it, and maybe you might want to do this 

1. just to be safe
2. because it may make for better file sharing

Format the slave drive as FAT32 and make that the partition to share files between the two OSes.
Resize the Windows partition on the primary master and install Ubuntu there (putting Grub on the MBR).

P.S. This is the best dual boot guide out there for Ubuntu:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by CaptainCrunch on 2005-11-28
[QUOTE=aysiu]You know, I've been thinking about it, and maybe you might want to do this 

1. just to be safe
2. because it may make for better file sharing

Format the slave drive as FAT32 and make that the partition to share files between the two OSes.
Resize the Windows partition on the primary master and install Ubuntu there (putting Grub on the MBR).

P.S. This is the best dual boot guide out there for Ubuntu:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)[/QUOTE]

I'll read that when I get a chance tomorrow.   I'm not too worried about sharing stuff between OS's.   If I really need something, I'll use a DVD-RW to transfer, since CDFS is universal, or perhaps a small FAT32 partition on the 60GB drive.   I don't really feel like resizing, granted I have System Commander 7.

---

