---
title: "How do I partition?"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by Medeo on 2005-11-12
Brand new machine, no other OS currently, trying to install Ubuntu 5.10. It gets as far as the part where I need to partition the disk, and that's where I run into problems. Although it tells me that I have the option of partitioning manually or with the installer's help, it only lets me choose manual for some reason. So I choose manual, and it takes me to a menu where I have no clue what to do next. If I tell it to just go ahead and continue with the installation, it just tells me that the disk isn't partitioned; even though I only plan on having just the one OS.

I only have one HDD, an S-ATA 80GB. I have no idea what to do at this point- I've never installed an OS before, and I've only tangentially used Linux in the past (too little, and too long ago, to matter).

Thanks for your help.

---

### Post by sheenaramone on 2005-11-12
[QUOTE=Medeo] Although it tells me that I have the option of partitioning manually or with the installer's help, it only lets me choose manual for some reason. [/QUOTE]

Sorry if this is a dumb answer but sometimes you have to use tab to move between selections during setup.  It will say in the screen what you have to do to navigate.  I ran into that this morning.  If the arrows wouldn't work for me, I needed to use tab.

Sheena

---

### Post by yesplease on 2005-11-12
On a 80GB disk I would make three partitions / (root) 5GB, swap 1GB (less than 2GB for i368 ), and /home.

Choose manual partitioning during install. Select the disk and go to basic settings.

root partition; use as Ext3, format yes, mount point /, mount options default, bootable flag on, size 5 GB.

Swap partition; use as swap, bootable flag off, size (less than 2 GB), format yes


home partition; I have no notes, from memory: use as Ext3, format yes, mount point /home, bootable flag off, (mount options default I guess), size choose remainder of disk. 

I remember there is also a question like put this partition at the beginning, where I always answer yes.


Because you do not need to preserve a Windows partition on your disk, this is not a dangerous operation.

---

### Post by Medeo on 2005-11-12
Huh. Well, it turns out that it can't find the HD, which may be part of the problem :). I'll hunt around some other forums to see if I can't fix that, then get back to you. Ah, the joys of building a computer from scratch ](*,).

Thanks for the suggestions, though.

---

