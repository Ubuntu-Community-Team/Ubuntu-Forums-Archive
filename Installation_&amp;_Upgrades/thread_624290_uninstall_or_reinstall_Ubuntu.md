---
title: "uninstall or reinstall Ubuntu"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by alphawill on 2007-11-26
I'm trying to fix the sound on Ubuntu, but still no success.  I think I just compiled to many files and the sound still doesn't work.  Is there any way to reinstall?  If not how do I just uninstall it?

---

### Post by human-ness on 2007-11-26
I installed Gutsy as an update, so I cannot comment on how the CD installs.  It may do the same as the Feisty CD and format the HD.

You should be able to safely backup your home directory and then install Feisty over the top, as it formats the Linux partition for you, before installing a fresh copy.  Once it's installed again, copy the backup of your home directory, over the top of the new one.

In case I am missing something out here, wait for a few more replies before doing so, because I have not had to reinstall Ubuntu that often at all.

Good luck.

---

### Post by mikewhatever on 2007-11-26
The re-installation process is very similar to the initial installation. The only difference would be at the partitioning stage. You do not need to resize or create new partitions, since they are already set up the way you want. Choose the manual option, and edit each partition's mount point by right clicking on it. You must specify your / and swap mount points, and you'll need to format /. All data will be erased during formatting, so backup if necessary.
Post the output of <sudo fdisk -l> if you do not know which partition is which.

---

### Post by alphawill on 2007-11-26
Wow what fast responses.  Thanks guys for the help

---

### Post by alphawill on 2007-11-27
> **mikewhatever said:**
> The re-installation process is very similar to the initial installation. The only difference would be at the partitioning stage. You do not need to resize or create new partitions, since they are already set up the way you want. Choose the manual option, and edit each partition's mount point by right clicking on it. You must specify your / and swap mount points, and you'll need to format /. All data will be erased during formatting, so backup if necessary.
Post the output of <sudo fdisk -l> if you do not know which partition is which.

If you don't mind could you guide me through this process.  I'm a total noob, and I'm trying to learn everything

---

### Post by mikewhatever on 2007-11-28
> **alphawill said:**
> If you don't mind could you guide me through this process.  I'm a total noob, and I'm trying to learn everything

Ok. Can you post the output of <sudo fdisk -l>.

---

### Post by alphawill on 2007-12-03
> **mikewhatever said:**
> Ok. Can you post the output of <sudo fdisk -l>.

Sorry about the late reply.  I didn't see that you responded back.  Also finals have been killing me, with this stress so I've tried to not let it stress me out as much, but here it is

> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69bd10d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        6482    50524414+   7  HPFS/NTFS
/dev/sda3            6483        9589    24956977+  83  Linux
/dev/sda4            9590        9729     1124550    5  Extended
/dev/sda5            9590        9729     1124518+  82  Linux swap / Solaris

  ...


Also in the process of trying to fix my sound I by mistake made 3 different Ubuntu start-ups

I now have 

Ubuntu 7.10 386
Ubuntu 7.10 ume
Ubuntu 7.10 generic
:(

Why do I do these things to myself:confused:  Please help.

:(

---

### Post by mikewhatever on 2007-12-05
This has perfect timing, since I've just finished reinstalling and updating from Feisty to Gutsy. The memories are could not be fresher.
In you set up, sda3 is / and sda5 is swap. The only work you'll have to do while reinstalling is setting appropriate mount points for the two. That can be done by right clicking on a partitions and choosing Edit. The mount point is specified in a box in the middle. Remember, / for sda3 and swap for sda5. All the other partitions should be mounted automatically. By the way, what's on sda1?

---

### Post by alphawill on 2007-12-05
I don't even know.  I better just leave it alone though.  I don't want to break anything.  Thanks for the help.

Do you think you could answer though why I have those three opitions and their alternatives?  I would delete it, but I don't know what's on it.  Would it be safe.  I have back-ups of what I need on Vista, so if its gone, nothing would be missed.

---

### Post by mikewhatever on 2007-12-07
The three options are three alternative kernels you must have installed at some point. Generic should ususally be the default one, 386 is for older hardware, and I do not know about the third one. Decide which one you need, or perhaps all three, and remove the unneeded from Synaptic.

---

