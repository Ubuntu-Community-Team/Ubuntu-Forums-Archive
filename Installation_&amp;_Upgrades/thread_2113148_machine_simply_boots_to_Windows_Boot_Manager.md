---
title: "machine simply boots to Windows Boot Manager"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by UberStudent on 2013-02-06
Trying to install 12.04 LTS on an HP Pavillion dv7 with AMD and Windows 7.

Followed the steps in [https://help.ubuntu.com/community/UEFI#Setup_the_BIOS_in_EFI_or_Legacy_mode](https://help.ubuntu.com/community/UEFI#Setup_the_BIOS_in_EFI_or_Legacy_mode)

Now the machine simply boots to Windows Boot Manager, asking me to insert my Windows Installation Disc (which I don't have).

First run of Boot Repair URL: [http://paste.ubuntu.com/1617638](http://paste.ubuntu.com/1617638) 

Second run of Boot Repair URL: [http://paste.ubuntu.com/1617658](http://paste.ubuntu.com/1617658) 

Please help! I have a presentation to give tomorrow!

---

### Post by darkod on 2013-02-06
You still didn't try to install right? Because there is no linux partition on the disk at all.

Try to go into BIOS and undo what you did following that tutorial. You are NOT using UEFI boot, so you don't need to do anything special.

But if you went into bios and changed the boot mode to UEFI, that might stop win7 working because it's not installed in uefi mode.

Note that when you do decide to install in the future, you will need to shrink some partition to make space for the ubuntu partitions, AND delete at least one partition because you currently have the maximum of 4 primary partitions. No more partitions can be created as it is. Which partition you delete, is up to you. Note that you usually can't delete the first or second, so you have to choose between the third and fourth.

---

### Post by Mark Phelps on 2013-02-06
I'm guessing that your fourth partition on the drive is HP_TOOLS -- which is why I included the material below:

Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

