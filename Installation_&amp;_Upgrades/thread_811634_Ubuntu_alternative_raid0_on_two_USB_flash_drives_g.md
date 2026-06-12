---
title: "Ubuntu alternative raid0 on two USB flash drives grub problem"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by markotitel on 2008-05-29
Hi,
I installed Ubuntu 8.04 with raid0 two usb flash drives.


All is working nice except I cannot boot into system.

Grub reports ERROR 2.

Whe I start Install CD and choose option BOOT FROM FIRST HARD DISK, my system boots and works.

Where I done wrong ?

Installing Ubuntu on single flash drive works, GRUB boots, but raid0 it can boot only with Install CD.

---

### Post by rich86 on 2008-05-29
According to the GRUB page Error 2 is this:
"2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system."

It would seem that your BIOS does not recognise the usb flash drives. You could try a bios flash to see if a new version has better support? If you look on the manufactures website they normally have a place of support and drivers. MAKE SURE YOU READ ALL INSTRUCTIONS BEFORE FLASHING it can make you system un-bootable if the process is not run correctly.
Hope that helps a bit,
Richard

---

### Post by markotitel on 2008-05-29
Thx for answer, 

Well maybe it is the problem but, when I install ubuntu on a single flash drive it boots without problems. So I guess it is not bios ? When I change BOOT order i BIOS for the usb flashes then I get GRUB ERROR 17 .

---

### Post by rich86 on 2008-05-29
Hurm, and just to be annoying GRUB error 17 is a bit vague, just seems to be a devise error with no specific error number. I am not really an expert on setting up RAID arrays so i am not entirely sure on their workings. Just to be clear though, how is your system set up at the moment? Sounds like you have two USB flash drives in a raid0 array and hard disk with GRUB on it that should tell linux kernal to load then run ubuntu from the usb sticks? That bit of extra information might help anyone else with more knowledge on raid.
Might be worth posting your menu.lst file as well.

---

### Post by markotitel on 2008-05-29
Hi,

I have just two USB flash drives, on first USB flash drive I made /boot partition, and then rest of free space marked use for RAID second usb flash is just raid .

Similar problem is solved here [https://answers.launchpad.net/ubuntu/+question/2115](https://answers.launchpad.net/ubuntu/+question/2115) , but I cannot understand it completely .

---

### Post by rich86 on 2008-05-29
Have you read this reply?
> 
 BrianH said on 2006-10-25:

It seems as if my SATA devices are in a different order when booting. I found a "Super Grub disk" that I wrote to a cd. When I boot using that it identifies the disk with the stage 1 on it as hd2. While in Linux grub shows it as hd0 as expected.

To get my computer running I've decided to not use raid1 on my boot partition. I installed Ubuntu again. It still wouldn't boot, so then I manually installed grub to the MBR of all of my disks, and pointed the grub setup (menu.lst) to hd2 instead of hd0. This setup allows the computer to boot properly.

Any ideas why the drives get assigned different hd numbers when booting? All four drives are plugged into the nvidia SATA controller on the MB and raid is disabled in the bios. I don't see any options for boot order among individual hard drives.

Could this be your problem, that the disk numbers are not the same when booting from grub or when booting using the cd. You could try experimenting with the drive letters in menu.lst and see if another combination works?

---

### Post by markotitel on 2008-05-29
I read it, and I cannot understand all of it. I tried to play with menu.lst and with grub. But cannot install grub on both drives, dont know why :( .
I get "does not have any corresponding BIOS drive" error .

---

