---
title: "OS Not Found (URGENT!)"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by DPic on 2007-12-02
Okay i have a bit of a lengthy problem. I decided to install Ubuntu on my family computer...without permission but i figured it would be fine since i've already installed it on three of the computers in the house without a problem and been using it on my own without windows for over a year. Anyways, enough about the situation, let's get down to the problem. 

Hard Drives--
The family computer has 2 HDDs in it. A 40 GB disk and a 120 GB disk. Both drives contain an installation of Windows (The installation on the 40 GB drive got messed up and we got a new hard drive so there is now an installation on the larger drive as well but there were still some things that hadn't been moved from the old drive). 

Partitioning--
The LiveCD didn't work because of some display issue. It's an old computer and in case you were wondering it has an nvidia geforce2 mx/mx 400. Using the alternate CD, i tried partitioning that 120 GB drive since that one was mostly empty but for some reason it was unable to so i partitioned 5 GB off the 40 GB drive instead (ubuntu only requires 4). 

GRUB--
Well the installation all went fine until it came to installing GRUB. Grub asked me if whether or not to install it to the master boot record, listed one installation of windows, and told me that i would be able to boot the listed operating systems if i were to install GRUB to the mbr. I said no since the other installation of windows was missing, and it asked me where to install it to instead. 

It wasn't really clear on what the options were. It just listed the mbr, and two drives, on of which was on the same sick as the mbr. I'm too tired at this point to remember my reasoning but it was an admittedly stupid move. I tried one of the drives for whatever reason and it didn't work so i tried the other one and the installation was successful. HOWEVER, when the computer booted up, it just said No operating system detected or something along those lines. The BIOS didn't even come up. 

PLEASE, help me if you know how. My dad is gonna kill me if i don't have a solution by tomorrow!

---

### Post by PmDematagoda on 2007-12-02
When the PC starts up press Del or F2 to enter the Setup, once there change the boot priorities of the Hard Disks from the first one to the second one.

---

### Post by confused57 on 2007-12-02
If booting first to the other hard drive doesn't help, you can always burn a Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You can see if SGD is able to boot Ubuntu and it's also capable of restoring your Windows IPl to the mbr, by selecting "Fix Boot of Windows".

---

### Post by DPic on 2007-12-02
So we've concluded that it was a problem with the mbr. I haven't found a windows disk to fix the mbr with so i went back to the install disk to just install grub to the mbr. Unfortunately, when i got there, i discovered a new problem. Before installing grub i have to complete the partitioning part of the installation and specify where all the drives are mounted but this time, i got an error saying that the filesystem was the wrong size "for windows to like it."

---

### Post by DPic on 2007-12-02
Alright, so i decided that since even though the install disk told me that the file system on the smaller drive for windows was smaller than windows thought it was, i would continue ignoring that message for now because i wasn't going to make any changes to that drive. I was just reinstalling ubuntu the the partition i had already created for it. 

After that, i could get into linux, but i need to get GRUB to pick up windows on the other hard drive. I already tried this [http://www.gnu.org/software/grub/manual/html_node/Chain_002dloading.html#Chain_002dloading](http://www.gnu.org/software/grub/manual/html_node/Chain_002dloading.html#Chain_002dloading) 
 but i all i know is that the hard drive that still contains windows is sdb1 so i tried grub> rootnoverify (sdb1,0), grub> rootnoverify (sdb1,1) and they both returned an "Error while parsing number"

I'm also going to have to figure out how to tell my parents i wiped the drive....

---

### Post by confused57 on 2007-12-02
> **DPic said:**
> Alright, so i decided that since even though the install disk told me that the file system on the smaller drive for windows was smaller than windows thought it was, i would continue ignoring that message for now because i wasn't going to make any changes to that drive. I was just reinstalling ubuntu the the partition i had already created for it. 

After that, i could get into linux, but i need to get GRUB to pick up windows on the other hard drive. I already tried this [http://www.gnu.org/software/grub/manual/html_node/Chain_002dloading.html#Chain_002dloading](http://www.gnu.org/software/grub/manual/html_node/Chain_002dloading.html#Chain_002dloading) 
 but i all i know is that the hard drive that still contains windows is sdb1 so i tried grub> rootnoverify (sdb1,0), grub> rootnoverify (sdb1,1) and they both returned an "Error while parsing number"

I'm also going to have to figure out how to tell my parents i wiped the drive....

Maybe the entry in this thread will work:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

