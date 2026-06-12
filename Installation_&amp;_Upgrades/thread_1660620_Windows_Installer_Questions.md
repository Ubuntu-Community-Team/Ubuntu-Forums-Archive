---
title: "Windows Installer Questions"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by Zoomy on 2011-01-05
I have installed Ubuntu 10.04 on three older computers with sluggish Windows, and each time I have used the WUBI installer so that I can dual-boot.

About 3 years ago, I was able to boot a Ubuntu install disc, and configure dual booting with Windows without too many problems, however now I cannot figure out how to do this now.

Question One:  Is it possible to boot Ubuntu 10.04 from CD and configure a dual boot system?  Each time I've attempted this, all choices seem to lead to eradicating the old partition.

Question Two:  I have a system now that is dual booting Windows and Ubuntu, but the machine needs a clean install of Windows XP Home on the Windows partition.  Is this possible without disurbing the GRUB menu?

Thanks,

---

### Post by jaythedogg on 2011-01-05
Now I am no expert, but I believe you can reinstall Windows without disturbing the Grub loader. I say this because when I went to install Windows, it asked me if I wanted to format C or dual boot with my old OS... Then again, is the boot info in the Windows directory or is it in the master boot record *outside* the windows partition? 
Not entirely sure, but maybe one of the guru's can help you...

[SIZE="1"][...Then pop over to my thread & help me with my infuriating headache maker! Click here btw...]("http://ubuntuforums.org/showthread.php?t=1660499")[/SIZE]

---

### Post by Frogs Hair on 2011-01-05
I set up the Ubuntu partition from Windows disk management by shrinking the free space. When I come to the partition portion of the Ubuntu installation , I choose that partition and there is no chance of overwriting anything.

---

### Post by ekjsim on 2011-01-05
Maybe, you should just delete all partition, and resize your HDD with Windows. Then, you should use the windows installation disk to repair the MBR. Get a new grub and a new ubuntu OS.

---

### Post by presence1960 on 2011-01-05
> **Zoomy said:**
> I have installed Ubuntu 10.04 on three older computers with sluggish Windows, and each time I have used the WUBI installer so that I can dual-boot.

About 3 years ago, I was able to boot a Ubuntu install disc, and configure dual booting with Windows without too many problems, however now I cannot figure out how to do this now.

Question One:  Is it possible to boot Ubuntu 10.04 from CD and configure a dual boot system?  Each time I've attempted this, all choices seem to lead to eradicating the old partition.

Question Two:  I have a system now that is dual booting Windows and Ubuntu, but the machine needs a clean install of Windows XP Home on the Windows partition.  Is this possible without disurbing the GRUB menu?

Thanks,

#1- Yes, absolutely. there are two ways to do so. First you should look in disk management and make sure you don't have 4 primary or 3 primary and an extended partition with no unallocated space in the extended. Otherwise you can shrink windows C: from disk management to create space for ubuntu. Then boot the ubuntu Live CD and install ubuntu to that unallocated space. Or after creating unallocated space you can boot the ubuntu Live CD to desktop and use gparted to create partitions for ubuntu from that space then choose manual install to install to those partitions.

The second method is to boot the ubuntu Live CD and when installing choose "install side by side". You can then use your mouse to grab the right side of the windows partition and slide it to the left until you have allotted the amount of space you want for ubuntu.

#2-The GRUB menu won't be disturbed because that is located in your grub.cfg file in GRUB2 installs and menu.lst file in Legacy GRUB installs. However windows will overwrite GRUB bootloader on the MBR. You will have to reinstall GRUB to MBR with the ubuntu live CD/USB. The method of doing so will differ according to whether you use GRUB2 or Legacy GRUB.

---

### Post by presence1960 on 2011-01-05
> **ekjsim said:**
> Maybe, you should just delete all partition, and resize your HDD with Windows. Then, you should use the windows installation disk to repair the MBR. Get a new grub and a new ubuntu OS.

Now why in the world would you do all that just to add or reinstall windows? That is definitely the WORST way to accomplish the task at hand.

---

