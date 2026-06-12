---
title: "Installation on top of 2 distros"
date: 2006-02-25
forum: Installation &amp; Upgrades
---

### Post by damu on 2006-02-25
I have Win XP and Studio to Go!(knoopix based distro dedicated to audio production) installed on my desktop. I want to install Ubuntu, as my 
main - everything but audio production- distro. 

I had already 4 primary partitions on my main hardrive (1: NTFS for Win Xp, 2: Ext3 for STG!, 3: swap, 4: fat 32 for documents)...

So, I erased 3 & 4. In the free created  space, I created 3 logical partitions (ext 3 for ubuntu, swap to be used by both linux distros, and fat32 for data shared in between all distros).

I did this in the partition manager of Ubuntu installation, and then it asked me to deal with LVM. I don't have a clue about how to deal with LVM and all the different options. However, I never managed to install on the created partitions.

I finally gave up, restarted on Win XP to make sure my GRUB was still ok, and to ask for your help.

I can see on my partition manager the logical partitions which have been created. But Ubuntu wouldn't offer me the possibility to install on it.
From WinXP, the hard drive actually looks like this :

C - primary - NTFS  ...Win XP
* - primary - ext3    ...STG!
* - logical  - ext3     ...Ubuntu
* - logical  - swap
* - logical  - fat32    ...data

I also have another SATA hard drive in ext3, which is only used for datas.

Any clue on how I can install Ubuntu on this logical ext3?
Thanks,

---

### Post by damu on 2006-02-27
Well, I managed to go round that one by erasing the logical ext3 and swap.
Then I chose the option of letting Ubuntu installer deal automatically with the free space available.
So now, I have another issue :

only one partition (hda3 where Ubuntu is installed) is seen and mounted in "media". 
The logical fat 32 partition with all my datas is not there. 
I can't see either my second sata hard drive.
I could see them at the partitionning step during the installation though.

How to round that? Do I need to change the fstab?

Thanks

---

### Post by hankeral on 2006-02-28
Damu
I just installed Breezy on my multiboot machine. I have several linux distros as well as Win98SE and WinXP the machine. As a point of reference, my fstab shows all of my partitions mounted under /media. In addition, the GUI shows icons for each operating system and the DVD and CDROM drives when media are installed in them.
What does your fstab show? Which boot loader are you using ?
I'm using the XP loader.

---

