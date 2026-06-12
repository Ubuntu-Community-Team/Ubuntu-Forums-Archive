---
title: "Dual boot system help!!"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by JonDO7 on 2012-05-05
I have a simple problem. I am running Ubuntu 11.0 and Ultimate Edition 3.0 on the same hard drive. My question is, how can I configure my hard drive to run one  of the operating systems and delete the other? I realize that is I do this, I will need to reconfigure grub. Now I have done this before with a Windows /Ubuntu dual boot system (and it is quite easy to do), but never with a dual Ubuntu boot system. Can anybody help me figure out how to delete one of the OS`s and repair grub to run the OS that I want? I am guessing that I will have to use GParted, I just don`t know how to delete the partion and fix grub.  Any help would be extremely helpful!! Thanks!

---

### Post by 2ta8gdfte on 2012-05-05
Just post what you have and what you want to keep, and it should be fairly straight forward. Post the output of this command in the ubuntu terminal as well.

```
sudo fdisk -l
```

---

### Post by darkod on 2012-05-05
The first thing is to make sure you have grub from the OS you want to keep on the MBR. For this, the fdisk results you were asked for above will help. But if you have only one hdd, we don't even need them for this.

If you only have one hdd, boot the OS you want to keep and in terminal do:
sudo grub-install /dev/sda

That will install grub to the MBR, from the OS you are running currently, in other words the one you want to keep.

When you have that sorted out, it's simply deleting the partition(s) of the other OS and using that space as data partition, for example. If you need help with this post the fdisk results or even better a screenshot of Gparted.

---

### Post by JonDO7 on 2012-05-05
Well I tried to do what you asked and this is what came up:

ondo7@jondo7-Inspiron-530 ~ $ sudo fdisk -l
[sudo] password for jondo7: 

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b2a3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16290   130844227   83  Linux
/dev/sda2           16290       30395   113294337    5  Extended
/dev/sda5           30003       30395     3142656   82  Linux swap / Solaris
/dev/sda6           16290       29612   107006976   83  Linux
/dev/sda7           29612       30003     3137536   82  Linux swap / Solaris

Partition table entries are not in disk order
jondo7@jondo7-Inspiron-530 ~ $ 
jondo7@jondo7-Inspiron-530 ~ $ sudo grub-install /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
jondo7@jondo7-Inspiron-530 ~ $ 

The first partition is the one I want (/dev/sda1) so that is what I did enter, but it looks like it didn`t work for som reason. Any sugestions?

---

### Post by wilee-nilee on 2012-05-05
Your command

```
sudo grub-install /dev/sda1
```Darkod's command.

```
sudo grub-install /dev/sda
```sda1 is the partition, sda is the mbr run the command again. I assume you see the difference now. :)

I mainly had you run the fdisk to confirm what is there and that none were a windows wubi install, one never knows just being safe.

Ignore the other user name it is along story lol.

---

### Post by JonDO7 on 2012-05-06
Ok! Every thing has worked up to this point. The system boots up to the OS that I want to use, just the way you explained it. Thanks!
Now my next problem is, after deleting the other partition, how can I extend it, so that the other partition can be added to the OS partition? I used GPated to delete the other partition, then reformatted it to FAT32. But for some reason I can not add it to the other partition.. I am kind of new at using  the tools for these operating systems, but after using windows for so long, I have found alot of advantages using Linux systems. Please pardon my ignorance and thank you so much for your help so far!!

---

### Post by wilee-nilee on 2012-05-06
> **JonDO7 said:**
> Ok! Every thing has worked up to this point. The system boots up to the OS that I want to use, just the way you explained it. Thanks!
Now my next problem is, after deleting the other partition, how can I extend it, so that the other partition can be added to the OS partition? I used GPated to delete the other partition, then reformatted it to FAT32. But for some reason I can not add it to the other partition.. I am kind of new at using  the tools for these operating systems, but after using windows for so long, I have found alot of advantages using Linux systems. Please pardon my ignorance and thank you so much for your help so far!!

Take a screenshot of gparted looking at the HD and post it, it will be easier for me at least to know where you're at. Glad your set with the removal.

---

### Post by Farstanley on 2012-05-06
> **JonDO7 said:**
>  I used GPated to delete the other partition, then reformatted it to FAT32. But for some reason I can not add it to the other partition..
 
You can't expand a primary partition to include space from an extended or logical partition.
 
You would have to delete sda 2,5,6&7 and leave the space unused before expanding sda1. But leave 10Gb at the end of the disk and format it as a linux swap partition because some installations require it.

---

### Post by JonDO7 on 2012-05-06
Ok I have a file listed here as a screen shot. I have managed to delete all of the partitions accept one (a swap partition). And now how do I expand the primary partition? It still won`t let me resize it. Do I need to reformat the unallocated space before the other partition can be expanded?
The attached file is called screenshot1.jpeg

---

### Post by wilee-nilee on 2012-05-06
You actually have 3 partitions altogether, the sda1 the one to expand, the swap and the extended (the one with the green boarders) the swap is in.

So delete the swap you will have to possibly right click it to swap off  to remove it then remove the extended then right click the sda1 click  resize/move and expand it to the right leaving enough space for the ram  at the least equal to your ram, then make a swap partition and call it a  day.

The rule with swap is if you want to hibernate it needs to be equal at the least to the ram amount.

You probably know already but you need to use a live cd using gparted to move the sda1 at the least.

---

### Post by JonDO7 on 2012-05-06
Thank you guys for all the great help! I did every thing you said and extended the hard drive. I also made the new swap partition, then rebooted the system. All is well. Even though I am a newbee to Linux, I am really learning all the capabilities over windows that it has. And it`s free! I`m no tech, but I have been working with computers for almost 20 years. So I take my hat off to all you guys, for having the patience to give me the tech support to finish this job. Thanks again for your very quick reply’s also. 
Back in the day, techs would frown on newbees asking "dumb" questions.. So here`s to you guys for helping me out!!!

---

### Post by wilee-nilee on 2012-05-06
> **JonDO7 said:**
> Thank you guys for all the great help! I did every thing you said and extended the hard drive. I also made the new swap partition, then rebooted the system. All is well. Even though I am a newbee to Linux, I am really learning all the capabilities over windows that it has. And it`s free! I`m no tech, but I have been working with computers for almost 20 years. So I take my hat off to all you guys, for having the patience to give me the tech support to finish this job. Thanks again for your very quick reply’s also. 
Back in the day, techs would frown on newbees asking "dumb" questions.. So here`s to you guys for helping me out!!!

Generally it is a team effort here, glad we all could help.

---

