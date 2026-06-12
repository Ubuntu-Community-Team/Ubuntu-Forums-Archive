---
title: "Installing Ubuntu while changing grub"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by devilscemo on 2008-10-08
Hello everyone, i listened to a friend of mine and installed Archlinux... i hated it and want to go back to Ubuntu. The problem is this: I have a Grub which has Archlinux AND WindowsXP. I would like to install Ubuntu in the same partition Archlinux had and also keep a grub boot ( i don't want to have an XP boot i know it messes things up).. how can i do so? I do have UBUNTU and Windows Xp cds... thank you for your help

---

### Post by mlentink on 2008-10-08
I'd suggest booting the LiveCD, clicking on install, and at partition time choose manual and specify your current ext3 and swap partitions. Then let 'r rip...

---

### Post by devilscemo on 2008-10-09
hi I got my cd and tried 2 install...now i see the partitions are setup this way:
WINDOWS Xp || DOCUMENTS (NTFS) || OLD LINUX .. i also have a swap somewhere but I can't see it... i want to get rid of the old linux (so i delete the partition) and then put on the ubuntu one...
i use the same space as the old linux but i don't know what characteristics i should use:

Logical or Primary?
Location: Beginning or end?
Use as: ...? Ext3 Journaling File System? Ext2 File System? ReisersFS?? what is the difference?
Mount Point: ??

thank you for your help

---

### Post by caljohnsmith on 2008-10-09
About primary or logical partitions, really all you need to know to make that decision is that a HDD can have no more than 4 primary partitions, or the HDD can have 3 primary partitions and 1 extended partition, and within that extended partition you can have about as many logical partitions as your heart desires; so the extended partition is merely a container for the logical partitions. So if you want more than 4 partitions, you'll have to set up some logical partitions, but otherwise there is no need to have logical partitions. Be sure to keep Windows on a primary partition though.

The location of your Ubuntu partition shouldn't matter, and I would recommend using the ext3 file system. I don't know all the nitty-gritty technical details of the differences between ext3 and reiserFS or others though, but I know ext3 works well for probably more than 90% of Ubuntu users. :)

And the mount point of your main Ubuntu install should be root, or "/". Does that help or do you have more questions? :)

---

