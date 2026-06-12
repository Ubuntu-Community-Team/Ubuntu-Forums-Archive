---
title: "Partitioning Ubuntu/Windows Question"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by amorphouskev on 2011-05-29
I'm not sure if this is the correct category for this post (feel free to move if it isn't.)

Basically I've been using Ubuntu since 10.04 - I thoroughly enjoy it, and within 3 releases I've seen huge improvements with regard to usability and overall UI. 

Unfortunately I've caved to the pressures of the world, and will be switching back to Windows. Currently I have a partitioned HDD (I was going to attempt to install OSX on a partition I created, but never got it working).

So I'm wondering if I can reinstall Windows on my 2nd partition, and access my files on Ubuntu, copy them (music, vids, pics, docs) to my new Win partition, then expand so that it eats all of the Ubuntu space? Basically saving myself the extra few minutes of running to get an external hard drive.

---

### Post by zvacet on 2011-05-30
Shrink your Ubuntu partition and on that unallocated space install Windows.Then reinstall grub following [this]("https://help.ubuntu.com/community/Grub2#SIMPLEST - Copy GRUB 2 Files from the LiveCD")guide so you can access Ubuntu again.After transferring all files to  Windows partition do [this]("http://members.iinet.net.au/~herman546/p18.html#MbrFix.exe") to get Windows bootloader back and after that tyou can delete Ubuntu partition and add that space to Windows partition.I don't know if this method is faster then back up files to external drive. :)

---

