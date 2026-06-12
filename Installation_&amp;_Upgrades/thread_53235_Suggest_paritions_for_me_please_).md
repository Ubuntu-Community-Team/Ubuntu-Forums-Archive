---
title: "Suggest paritions for me please :)"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by web250 on 2005-07-30
Ok, so im finally ditching Windows completely. I've been dual booting with Kubuntu 5.04 , and it is just great. I'm now going to wipe my partition table and reinstall Kubuntu on the whole drive.

What would be the suggested route for partitions. I have a 120gb drive, and 1gb of memory.

I only have 1 user (me). So do I just put everything in one place (with swap seperate of course)? How big for swap? Also, i've been using ReiserFS, good idea?
Also, where do you all usually put folders for music, documents, etc.?

thanks.

---

### Post by jemt on 2005-07-30
Hi Web.

I can recommend the following layout :

Partition 1 : Swap - 1024 MB (You got plenty of space - let's make sure you don't run out of memory ;-)
Partition 2 : Root - X GB (I would probably say 10-20 GB - personally I use about 1.5 GB)
Partition 3 : Home - The rest.

It is a good idea to place swap at the beginning as it will improve performance. You also need a root partition (/). This one should also be placed as close to the beginning of your harddrive as possible. And besides that, you need what most people call a D-drive - your personal drive that contains personal information, profiles etc. By creating a Home-partition all your profiles are saved, and you can reinstall Ubuntu without loosing your settings.

---

### Post by az on 2005-07-30
If you are going to reinstall, I cannot think of a reason for you to not just close your eyes and use the entire disk.  Use guided partitioning.

Ext3 is fine.

All one partition is fine.

Let the installer pick the size of your swap.

---

### Post by jemt on 2005-07-30
Azz > IMO One disk is never a good solution. If he want to reinstall his system, he will haft to move all his data to an external source or back it all up on ie. CDs/DVDs.

---

### Post by web250 on 2005-07-30
[QUOTE=azz]If you are going to reinstall, I cannot think of a reason for you to not just close your eyes and use the entire disk.  Use guided partitioning.

Ext3 is fine.

All one partition is fine.

Let the installer pick the size of your swap.[/QUOTE]

Ok. But is it OK to use ReiserFS, isn't it faster? Should i have a seperate /boot partition, ive seen that as a popular option?
I've seen:
/boot 100M
swap 1gb
/    20GB
/home rest

is that a decent setup?
should i vary my filesystems? Should /boot be ext3 and / and /home reiserfs?

---

### Post by DJ_Max on 2005-07-30
Don't know why exactly, but the rule of thumb is to make the swap 2x the amount of Ram you have available. So I would make your swap 2GB. 

Like azz said, let the installer do everything for you, unless you have special needs.

---

### Post by az on 2005-07-30
If you are serving a few hunded pages per minute and need to access a very populated filesystem with several million files in it, ReiserFs will help you out.  If you are burning cds and browsing the web, you will never come close to seeing any benefit from ResiserFS.


...And if you want to reinstall again it is up to you whether backing up all you data to a removable disk or cd is simpler than making another partition.  It depends on what you have.

---

