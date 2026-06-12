---
title: "Issues with dd - insight anyone?"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by three_jeeps on 2010-10-26
I have a 20GB ata disk with ubuntu server 8.04 LTS installed and running a number of servers (apache, hylafax, mail).  I want to clone the disk, so I connected a CD-ROM to the server, booted Ubuntu live CD 10.10 and then plugged in a 40 GB USB disk that is to be the target of my image copy.I put a partition table on the 40 gb disk and formatted it.
I unmounted both disks, an ran: fi=/dev/sda  fo=/dev/sdb.
Things chugged along and then dd appeared to hang (after about 1.5 hrs).  Repeated the image copy with same result.  I check the target disk with gparted, it said the entire 40 gb disk was unallocated.  Weird.  So I figured what the heck, I popped the 40gb disk in the machine and booted.
Boot did a fsck and said OS was write protected, manually run fsck and fix.
Now I am stuck...don't know what to do.  Don't know how to fix...
Suggestions?
J

---

### Post by three_jeeps on 2010-10-27
Hmmm, well I solved the problem by using Clonezilla.  FWIW, if one wants to make a bit by bit copy with a program that has some useful information and visual feedback, Conezilla is the way to go. It informs the user what it finds on the source disk, provides information on the target disk, informs the user that it is copying mbr, that the partition table is copied, etc. A lot better than running dd, not getting any feedback, and waiting for the prompt to come back. I tried dd with various sizes and got the same behavior....never returned to the prompt. 

After cloning, I looked at the disk with gparted and it was happy with everything it saw, e.g. no complaints about anything.

Another consideration is that dd and gparted run under a live CD version of the OS.  I tried Debian, Ubuntu, and Knoppix live distros and all three were sluggish at best on my machine.  Clonezilla boots its own environment with minimal OS support and is peppier.  Wish I would have used Clonzilla initially, it would have save me a *lot* of time.

---

