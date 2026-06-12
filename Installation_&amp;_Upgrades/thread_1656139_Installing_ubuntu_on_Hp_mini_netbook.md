---
title: "Installing ubuntu on Hp mini netbook"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by elcaballero_carmelo on 2010-12-30
Hi all, 
I have recently purchased a hp mini netbook, and would like to install ubuntu on it, preferentially along with windows 7. The thing is that the hard disk has already 4 primary partitions: C: (where windows 7 is), D: (recovery, to reinstall windows if necesary), and two hidden partitions: System and tools, containing the bios and some other stuff. So, when I boot from the ubuntu flashdrive, linux runs nicely, then I try to install and linux gives me only the option of using the whole hard disk, no option to install it toghether with windows 7. If I enter the partition tool, and split C:, the remaining space appears as not usable, and not as free space!, therefore I can not create a partition for linux. I have been reading in other forums that the maximum primary partitions allowed are 4, and as my harddisk already has 4 ... I can not create one for linux. Some people have suggested just using wubi. Other people have suggested deleting the D (recovering drive, previosly making a backup of it), so that there will be only 3 partitions left, and I can create a 4th one for linux.
What do you people suggest? Have anybody had a problem like this?. 
What would happen if I delete C: and use this for linux (of course I will lose windows).
Thanks!!!

---

### Post by ottosykora on 2010-12-30
Yes , I have read that this strange setup is getting to bad habit of HP.

You will need probably first some external hard drive, to be able to copy at least one of the partitions to it first. Then you can delete the partition you just backed up. 
Shrink the other partitions , then create in the free space an extended partition. Note: the extended partition is the 4th primary now.
In this you can create logical drives, many logical drives and it will not break the 4prim partitions rule any more. One will be for the before saved partition, next for the ubuntu, one more could be for the /home directory, one small could be created for swap.

Also note, that if some of the partitions are dynamic drives, then they will have to be converted to basic with the windows driver manger first.


Then you can restore the backed up partition to the place created for that and then you can start installing the the ubuntu.


For the work with partitions, you may want to use dedicated software as gparted for example and directly the installer of ubuntu in first place.

---

### Post by kgarbutt on 2010-12-30
My son recently deleted a hidden partition on his HP Windows 7 laptop and had to purchase from HP some recovery disks. So I would say before you do anything -- please make some recovery disks as HP typically doesn't give them to you any more.

---

### Post by elcaballero_carmelo on 2010-12-31
Hi thanks for the answers!
Two questions, one for each one of you:
 
1- If I create an extended partition, the logical partitions inside it, can one be ntfs and the other ext3, or only one kind of file system is allowed?
 
2- Where from did your son get the disks? how did he install them, if the hp mini has no disk driver? an external disk drive? does the bios automatically recognice this external device?
 
thanks!

---

### Post by rng on 2011-06-07
I am having the same problem.

elcaballero_carmelo: how did you solve your problem? 

Has anyone got any further information on it?

I found another thread with more info: 

[http://ubuntuforums.org/showthread.php?t=1652358](http://ubuntuforums.org/showthread.php?t=1652358)

---

