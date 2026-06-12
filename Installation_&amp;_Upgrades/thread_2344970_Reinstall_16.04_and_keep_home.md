---
title: "Reinstall 16.04 and keep /home"
date: 2016-11-29
forum: Installation &amp; Upgrades
---

### Post by marciano#1 on 2016-11-29
I already have installed 16.04 in a disk live DVD had formatted (three partitions, one small in FAT32, another SWAP and the large one EXT4).
/home is in the same partition as system
I want to reinstall the system.
From a live DVD 
[LIST]
[*]Checked Download updates....
[*]Checked Install third-party....
[/LIST]
Continue
[LIST]
[*]Selected 'Something else' because the option 'Erase ubuntu and reinstall' erases everything (photos, music... are in /home)
[/LIST]
The Disk is /dev/sdb
[LIST]
[*]free space    1MB
[*]/dev/sdb1 fat32  536MB  33MB used
[*]/dev/sdb2 ext4  491044MB  186354MB used
[*]/dev/sdb3 swap  8522MB  unknown
[*]free space    1MB
[/LIST]

Selected /dev/sdb2 ext4 
Device for boot loader installation:  Selected the same but I got this message:
[I]No root file system is defined.
Please correct this from the partitioning menu[/I]

I don't have that partitioning menu to set the Mount Point at this point of installation.

What to do? 
Thanks

Edit 1: I belIeve I got it: In Edit partition despite the disk is already formatted as ext 4 I have  to set again "Use as -Ext4..."  **After that**, Mount point is displayed
Edit 2: I don't know how to mark this post as **SOLVED**

---

### Post by TheFu on 2016-11-30
See the "thread tools" above?  Help us out, please.

---

