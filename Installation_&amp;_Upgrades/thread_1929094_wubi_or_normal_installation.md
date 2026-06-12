---
title: "wubi or normal installation?"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by Harikrishnanu on 2012-02-21
I have windows 7 installed in my pc , should i install ubuntu 11.10 through wubi or the normal installation and which is better to do. which is easier? please help. thank you in advance.

---

### Post by mastablasta on 2012-02-21
Wubi is easier, but normal (side by side dualboot) install is better. Wubi uses a virtual file inside windows and is of limited size as well as it has osme other issues. hwoever it is good if oyu want to give it a try to the OS.
 
Another option (also good to try out the OS) is Virtualbox install if you have enough ram.

---

### Post by darkod on 2012-02-21
A normal dual boot is much better, especially for long term install. Wubi was never developed to be used as long term install and very often updates or upgrades can break it.

---

### Post by Mark Phelps on 2012-02-23
Personally, would recommend dual-boot install, with Ubuntu in its own partitions.

But, before you do that, strongly suggest you read through the following:

Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

