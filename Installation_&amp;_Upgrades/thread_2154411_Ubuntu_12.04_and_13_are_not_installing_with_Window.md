---
title: "Ubuntu 12.04 and 13 are not installing with Windows. Help needed!!"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by panjgoori on 2013-06-14
Hello everyone. this is my first post here. today i tried to install Ubuntu 12.04 and 13.04 along with Windows 7. when my laptop boots from Ubuntu dvd and show me whether i want to install or try ubuntu. When i select Install Ubuntu>then some options and after them it offers me how i want to install Ubuntu. When i select Alongside with Windows 7 instead of Continue button it gives me Restart to continue option.

But when it restarts nothing happens.

Few days ago i tried to completely replace my windows installation with Ubuntu it completly formated my hard drive hence i lost all my files that's why i don't want to try this option. Any help will be appreciated. Thanks everyone.

---

### Post by oldfred on 2013-06-14
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Mark Phelps on 2013-06-14
> **panjgoori said:**
> Hello everyone. this is my first post here. today i tried to install Ubuntu 12.04 and 13.04 along with Windows 7. when my laptop boots from Ubuntu dvd and show me whether i want to install or try ubuntu. When i select Install Ubuntu>then some options and after them it offers me how i want to install Ubuntu. When i select Alongside with Windows 7 instead of Continue button it gives me Restart to continue option.

If you're attempting to use the Slider in the Ubuntu installer to shrink the Windows OS partition to make room for Ubuntu -- STOP!  Do NOT do that.  Shrinking the OS partition this way runs the risk of rendering Windows unbootable.

If you're serious about installing dual-boot then read through the details below BEFORE you attempt the install:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

