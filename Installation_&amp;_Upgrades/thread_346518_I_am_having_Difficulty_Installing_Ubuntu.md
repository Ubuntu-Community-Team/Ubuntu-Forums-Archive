---
title: "I am having Difficulty Installing Ubuntu"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by Grax123 on 2007-01-25
I got Ubuntu earlier today and I am having trouble installing it.  I put in the CD, clicked the Start or Install option, and ran the Installer.  It is doing fine until I get to partition hard drive.  I check the edit manually option and change them to my specifications.  Then I click forward.  It says something along the lines of installing 0 of 2 processes and after a little while and error message comes up, saying that the hdd can't be partitioned.  One of my friends said to reformat my laptop, so I tried and it said root file missing.  So I shutdown and tried to open up my Windows XP, but it is now gone from my Laptop.  Did I screw something up big time, or should I not partition my hdd, or what?  Can someone please help because now I don't have any OS on my Laptop.

---

### Post by logos34 on 2007-01-25
Boot from the ubuntu livecd again and load the desktop.  Open a terminal and type
> fdisk -l

Post it.  Windows (if there) will show up as '/dev/hda1' HPFS/NTFS 

Or, go to System>Administration>Gnome Partition Editor.  If windows (ntfs) partition is still listed, you're ok--it just was having trouble resizing it to make room for linux partitions.

Hopefully just windows bootloader is messed up, which is preventing you from starting windows.

---

### Post by Grax123 on 2007-01-25
I have the '/dev/hda1' HPFS/NTFS thing.  Run me through it really quickly, should I click On "Manually edit partition table", or should I pick this Option: "Resize IDE1 master, partition #1 (hda1) and use freed space".

---

### Post by Sef on 2007-01-25
A couple of questions:

1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

A suggestion:

Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

---

### Post by logos34 on 2007-01-25
> should I click On "Manually edit partition table", or should I pick this Option: "Resize IDE1 master, partition #1 (hda1) and use freed space".

In this case I'd choose the latter option.  

But doing what Sef suggested above wouldn't hurt...At the very least go back and verify the md5sum of your iso download and then do the 'cd integrity test' on the install menu screen.

---

