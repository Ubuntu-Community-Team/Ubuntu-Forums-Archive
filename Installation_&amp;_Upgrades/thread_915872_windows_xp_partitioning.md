---
title: "windows xp partitioning"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by lenswipe on 2008-09-10
My friend wants ubuntu installed on his laptop and i said i would do it.

Only thing is, his HDD is one big block and its not partitioned.

I want to partition his harddrive except when i open the microsoft management console under windows xp professional where i should normaly get a rightclick menu with a "New partition" option. I dont get the new partition option. 

Can an NTFS format be partitioned with gparted?


I would be grateful for any help offered.


Thanks alot.

---

### Post by snowpine on 2008-09-10
Hi Lenswipe, I would recommend backing up everything on the Windows partition, defragmenting it 2-3 times (from within Windows), then booting from the Ubuntu Live CD and running GParted.

I believe (not a Windows expert) your problem in this case is that you can't resize a partition while it is mounted and in use.

(edit) Yes, GParted can handle Windows partitions.

This page will help you plan the partitions: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by zwygart on 2008-09-10
Hi, I think that my experience will help you.

In december I installed Ubuntu on my desktop (1 HD 1 partition)
Ubuntu was able to boot but not windows. By installing MBR from Windows it was the invert. What I recommend you is to have at least two harddrives. One for XP, the other for Ubuntu. This way you can choose from BIOS. 

Be sure to keep boot MBR (XP and GRUB)

Sorry, I don't saw that you have a laptop
On my desktop, GRUB can't boot XP, but it's not matter, it works because of the two harddisks.

---

### Post by Zorael on 2008-09-10
> **zwygart said:**
> What I recommend you is to have at least two harddrives. One for XP, the other for Ubuntu. This way you can choose from BIOS.
That's not possible if he has a laptop with space for only one harddrive, though.

snowpine's advice is sound. Defrag first (and free up space in general, if needed), then use a live cd to resize and create new partitions.

---

### Post by timcredible on 2008-09-10
yes, you can partition the drive with ubuntu.  just boot up the livecd and double-click the install partition, there will be an option to partition your drive during the install.  there's a couple websites that have every step of the install process documented with screenshots, check them out if you want, should make it all clear.

---

### Post by Malac on 2008-09-10
This can be done at install time.
Boot to LiveCD then Install. at partitioning there is an option to resize partitions.

Just read the instructions carefully and as above backup anything/everything important before starting.

---

