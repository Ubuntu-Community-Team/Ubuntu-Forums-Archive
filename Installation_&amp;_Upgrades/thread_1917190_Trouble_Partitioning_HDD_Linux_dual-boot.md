---
title: "Trouble Partitioning HDD Linux dual-boot"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by optima4 on 2012-01-29
I originally installed Ubuntu 11.10 on the far left partition over the  whole HDD. A couple months later I dual-booted with Blackbuntu 10.10  (far-right). When I dual-booted 10.10 it automatically set the root,  swap, and home folder the way it is to the furthest right. (err.. two  swaps..?)

I want to install LMDE on this same HDD now. Originally I had planned to  overwrite everything on the far left, but due to some circumstances I  would rather shrink the partition and install it in the middle-- which  is where the unallocated 44 GiB came from. 

Now I am ready to install LMDE in the free space, but I have some questions.

1. How do I give the first partition to the far left a root, swap, and  home folder? Is that necessary? Should I use some of the unallocated 44  GiB to make these?

2. When creating the new parition what File System should I create it  to, and which should it be on Logical or other? How much space should I  give to each of these folders?

Some people say leave it on default, some people say it should be fat32, some say ntfs, what is the correct one?

3. In "System Monitor" under "Hardware" it says 2 GiB of "System Memory"  is required. So when creating the root, swap, and home folder, do they  each need 2GiB, or is that all together, or is that only for one of the  three?

---

### Post by BC59 on 2012-01-29
Just one swap partition is sufficient for all Linux OSs. You can delete the second without problem. 
You have a swap of 5.86GBs, it's huge. Depends of the RAM of your computer of course. How much RAM do you have?
You can install LMDE in the unallocated space you have (no more swap needed).

---

### Post by Triptol on 2012-01-29
Have a look at the grub config file. Grub is the program that allows you to select which OS (or effectively partition) to start during boot.

Please pay attention to the messages in the file: there are parts that you should not change, since your system will overwrite them. However you can change the other parts and add new OS-es.

This should get you started [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by optima4 on 2012-01-29
> **BC59 said:**
> Just one swap partition is sufficient for all Linux OSs. You can delete the second without problem. 
You have a swap of 5.86GBs, it's huge. Depends of the RAM of your computer of course. How much RAM do you have?
You can install LMDE in the unallocated space you have (no more swap needed).

Hey thanks so what you're saying is the other folders are already created? I don't need a root? I dont need a home? I hope that is all. I have been waiting to anything all day. So all I need to do is creat the unallocated space to Primary and ntfs or ext4, and I can move forward?


> Have a look at the grub config file. Grub is the program that allows you  to select which OS (or effectively partition) to start during boot.

Please pay attention to the messages in the file: there are parts that  you should not change, since your system will overwrite them. However  you can change the other parts and add new OS-es.

This should get you started [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Reading that now.

---

### Post by BC59 on 2012-01-29
If you like to delete the partition sda6, which as you said it was an old installation, boot to Ubuntu and then open the Disc Utility. On the left panel, choose your hard drive and to the right panel, you can find the partitions. The sda6 should be unmounted. In that case delete it pushing the button in the utility. The same for the unused swap partition. If it is unmounted delete it. If it's mounted, means it's working, don't touch it. 
After this you can boot with LinuxMint boot CD and install it. During the installation you can choose the space you like to be installed. Better choose the big unallocated space between sda1 and sda2. As file system better choose the ext4.

---

### Post by optima4 on 2012-01-30
Heres where I'm at now. I am getting somewhere at LinuxMint, but I am still stuck.

[http://forums.linuxmint.com/viewtopic.php?p=534357#p534357](http://forums.linuxmint.com/viewtopic.php?p=534357#p534357)

Any help would be greatly appreciated, although I feel I am pretty much being cornered into backing up my data and reinstalling. I can start that by a week or so from now. I really don't want to wait.

---

### Post by Triptol on 2012-01-31
> **optima4 said:**
> Hey thanks so what you're saying is the other folders are already created? I don't need a root? I dont need a home? I hope that is all. I have been waiting to anything all day. So all I need to do is creat the unallocated space to Primary and ntfs or ext4, and I can move forward?

Although you can share your home with multiple installations I would not recommend it (I have done it in the past). As soon as version of your Desktop are not in sync, the config files might not be compatible. What you need is a layout like this (all kind of variations can be applied here):

/sda1 -> first linux installation, including everything (home, boot, usr, lib, everything)
/sda2 -> 2nd linux installation, including everything
/sda3 -> swap. This one can be shared between the two installations.

Make all the partitions primary just for the sake of it (you can have 4 primary partitions, so you should be fine with this setup).

---

