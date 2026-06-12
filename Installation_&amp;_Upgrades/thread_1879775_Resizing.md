---
title: "Resizing"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by lm77054 on 2011-11-12
Hi all:  Well, I'm getting more and more confortable with UBUNTU.  Right now, I'm running UBUNTU as a windows app.  Now, I have a question for you fine folks.  I installed GPARTED within the Windows app'd UBUNTU, and it showed my physical drives (I have attached external HDDs).  Even in the Windows app'd UBUNTU, GPARTED shows the Windows Drive NTFS volume.  What I'm wanting to do, within the Windows app'd UBUNTU is to resize the main (system) partition.  When I run UBUNTU in a virtual machine (VM), and use GPARTED it only shows the VM, which I expected.  Is there anyway to resize (e.g. from 8GB to say 12GB) the Windows app'd UBUNTU without reinstalling it?  Thanks in advance!

---

### Post by Rubi1200 on 2011-11-12
Please don't try and use GParted or other partitioning tools with a Wubi install; it is a recipe for disaster!

Instead, use this guide by forum member bcbc, a Wubi expert:
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by coffeecat on 2011-11-12
I think I follow what you want, but you seem to be posing two different questions.

> **lm77054 said:**
> Even in the Windows app'd UBUNTU, GPARTED shows the Windows Drive NTFS volume.  What I'm wanting to do, within the Windows app'd UBUNTU is to resize the main (system) partition.

I read that at first as wanting to resize the Windows C: partition.

> **lm77054 said:**
> Is there anyway to resize (e.g. from 8GB to say 12GB) the Windows app'd UBUNTU without reinstalling it?  Thanks in advance!

And that sounds as though you want to resize the wubi virtual partition.

I think you are asking how to resize the wubi virtual partition and I simply misunderstood the first, but let's cover both anyway.

If you wish to resize the Windows C: partition you cannot do this with Gparted from inside a wubi installation because mounted partitions are not resizable, and the Windows C: partition is mounted permanently in a wubi installation - or at least those physically in the C: partition. If you wish to resize a Vista or Windows 7 C: partition, use Windows' Disk Management, not Gparted. If Windows XP, it's generally OK to use Gparted but from a live CD - or a Windows-based partitioner from inside Windows itself.

Anyway - to get to what you probably really want. The wubi virtual partition is the file C:\ubuntu\disks\root.disk and resizing this is a bit tricky, but doable. Have a look here:

[https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

Good luck!

**EDIT**: beaten to it by Rubi1200! :)

---

