---
title: "cant get past allocation of hard drive space on installation"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by dbranston4 on 2013-11-20
hi brand new to ubuntu have played around with it and want to install it permanently, alongside windows 7 but when i try to install it i get to the allocation of hard drive space and it just wants to restart my system or black screens i tried doing a partition in windows of unallocated space for it as i read somewhere it looks for unallocated space on the hard drive, it didn't recognise it so tried to allocate it to my drive c it wouldn't let me do that either.

i watched an installation process on youtube where the person mentioned something about 4 partitions could be an issue ( but he didnt go onto explain what exactley ) my drive does have 3 partitions part of the hp thing recovery, hp tools and then the main c drive. 

i have a hp g6 laptop any advice would be awesome as i so badly want to get ubuntu on my system by the way im trying to install 13.10 if that makes any difference 

i look forward to your responses 

Tortured

---

### Post by philinux on 2013-11-20
> **dbranston4 said:**
> hi brand new to ubuntu have played around with it and want to install it permanently, alongside windows 7 but when i try to install it i get to the allocation of hard drive space and it just wants to restart my system or black screens i tried doing a partition in windows of unallocated space for it as i read somewhere it looks for unallocated space on the hard drive, it didn't recognise it so tried to allocate it to my drive c it wouldn't let me do that either.

i watched an installation process on youtube where the person mentioned something about 4 partitions could be an issue ( but he didnt go onto explain what exactley ) my drive does have 3 partitions part of the hp thing recovery, hp tools and then the main c drive. 

i have a hp g6 laptop any advice would be awesome as i so badly want to get ubuntu on my system by the way im trying to install 13.10 if that makes any difference 

i look forward to your responses 

Tortured

You need to defrag windows a couple of times and use windows disk management utility to shrink the c drive to make some unallocated space for ubuntu. Assuming that you only have one hard drive and windows occupies it all in the c drive.

---

### Post by dbranston4 on 2013-11-20
> **philinux said:**
> You need to defrag windows a couple of times and use windows disk management utility to shrink the c drive to make some unallocated space for ubuntu. Assuming that you only have one hard drive and windows occupies it all in the c drive.


i defragged it once but did do the allocation with the disk management i will defrag it 3 times and try again hopefully that will do the trick the strange thing is it recognizes that there is spare space but wont let me allocate it. should i name the partition or just leave it unallocated 


There is only one hard drive seperated into 3 partitions and then there will be the ubuntu partition which would be the fourth.

---

### Post by sudodus on 2013-11-20
There might also be a hidden partition that makes a total of four primary partitions. You can check that when you boot a live session, 'Try Ubuntu without installing' from the CD/DVD/USB drive. If there are four primary partitions, you need to delete one to create 'logical space' for an extended partition, where you can have Ubuntu's partitions.

Are you prepared to run commands in a terminal window? Or would you rather use the file browser (corresponding to Windows Explorer)?

---

### Post by philinux on 2013-11-20
The max primary partitions is 4 but you can have many logical partitions.

You need to use the something else option. And make sure you've backed up anything important from windows. Just in case.
[http://www.youtube.com/watch?v=qBCHsgry2RQ](http://www.youtube.com/watch?v=qBCHsgry2RQ)

Vid is slightly out of date. Bits in the partitioner have changed slightly.

---

### Post by dbranston4 on 2013-11-20
> **sudodus said:**
> There might also be a hidden partition that makes a total of four primary partitions. You can check that when you boot a live session, 'Try Ubuntu without installing' from the CD/DVD/USB drive. If there are four primary partitions, you need to delete one to create 'logical space' for an extended partition, where you can have Ubuntu's partitions.

Are you prepared to run commands in a terminal window? Or would you rather use the file browser (corresponding to Windows Explorer)?

it does have a fourth partition i just found it its got tools, recovery, system, and then the c drive so i need to get rid of one of these then ?

---

### Post by yogi123 on 2013-11-20
[**[COLOR=#000000]You can make another "logical volume" of unallocated space. When you try install ubuntu you can see that drive , when you will create partitions for ubuntu file system. Windows can have only 4 "Primary Partitions" , not 4 "logical volumes".[/COLOR]**]("http://ubuntuforums.org/member.php?u=1883073")

---

### Post by dbranston4 on 2013-11-20
so just make them in the space that is available it does say it is unavailable though when i look at it through ubuntu instead of it being free space as shown on the you tube video phil posted

---

### Post by sudodus on 2013-11-20
> **dbranston4 said:**
> it does have a fourth partition i just found it its got tools, recovery, system, and then the c drive so i need to get rid of one of these then ?
Yes.

***First backup everything to an external drive, because what you intend to do is risky.***

Tools is the one that many people wipe. You can copy its content into a directory with the same name in another partition or in an external drive.

Then boot from another drive, for example an Ubuntu install drive and run ***gparted***.

Remove the tools partition. Now there is logical space for an extended partition, but do not create it yet.

The tools partition is probably small, not enough for Ubuntu. You need to houseclean Windows (remove things that only occupy space), shrink the main Windows partition (but leave space; at least 30% should be free for Windows to work well). ***Edit***: Shrink by moving the tail end of the partition. Keep the head end (the beginning or left end) at the original position! Otherwise you get problems booting Windows.

Create an extended partition of the largest chunk of drive space (as seen graphically in gparted). It is possible to install Ubuntu in 8 GB, but if you could get 20 GB or more after shrinking the Windows partition, it will last longer until you fill it with data.

[COLOR=#696969]There are more steps, but we can take those steps later on:

Then, if you wish, you can create an ext4 partition for the file system and a swap partition manually with gparted, or you can let Ubuntu do it half-automatic. I prefer gparted, because it is easier to see what I do, but it is your decision.

[/COLOR]

---

### Post by dbranston4 on 2013-11-20
> **sudodus said:**
> Yes.

***First backup everything to an external drive, because what you intend to do is risky.***

Tools is the one that many people wipe. You can copy its content into a directory with the same name in another partition or in an external drive.

Then boot from another drive, for example an Ubuntu install drive and run ***gparted***.

Remove the tools partition. Now there is logical space for an extended partition, but do not create it yet.

The tools partition is probably small, not enough for Ubuntu. You need to houseclean Windows (remove things that only occupy space), shrink the main Windows partition (but leave space; at least 30% should be free for Windows to work well). ***Edit***: Shrink by moving the tail end of the partition. Keep the head end (the beginning or left end) at the original position! Otherwise you get problems booting Windows.

Create an extended partition of the largest chunk of drive space (as seen graphically in gparted). It is possible to install Ubuntu in 8 GB, but if you could get 20 GB or more after shrinking the Windows partition, it will last longer until you fill it with data.

[COLOR=#696969]There are more steps, but we can take those steps later on:

Then, if you wish, you can create an ext4 partition for the file system and a swap partition manually with gparted, or you can let Ubuntu do it half-automatic. I prefer gparted, because it is easier to see what I do, but it is your decision.

[/COLOR]

space isnt an issue was planning on giving 100gb to Ubuntu and that would still leave me 300gb for the windows c drive so just to clarify 
copy the tools make a note of the size to recreate if it doesnt work then delete the tools partition allocate some space into free space from the main c drive to free up more space and then create the extra drive for ubuntu one primary and the swap logical  that right ?

---

### Post by oldfred on 2013-11-20
The only primary partition you are creating is the extended partiiton and often you do not explicitly create it, but create logical partitions which all will be in one extended partition. You can only have one extended paratition and it counts as one of the 4 primary partition allowed with MBR(msdos) partitioning.

I usually suggest when dual booting with Windows that you create a shared NTFS data partition. The Linux NTFS driver exposes all the normally hidden files & folders in WIndows so writing into the Windows system partition can lead to issues. If you have a separate shared NTFS data partition then less chance of issues. 

Same info as posted above. Most backup and delete hp tools partition.
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by dbranston4 on 2013-11-22
update i have 13 10 on vmware player now so pottering around on that decided that if i am happy with that then im just gonna kill windows there are some issues i would like help with but i will do a new thread for that thank you everyone for your help :)

---

