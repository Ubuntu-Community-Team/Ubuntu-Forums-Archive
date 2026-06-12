---
title: "Installation proble"
date: 2013-04-21
forum: Installation &amp; Upgrades
---

### Post by venkatamanne on 2013-04-21
Hi all,
I have formatted my USB and used [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") to boot usb..
then i set boot option 1 as usb and i restart......it asks me to choose whether i want to install along side windows7 that i already have or i just want to go with ubuntu....when i choose 1 st option it says continue....when i click on continue ....then it says system is going down to reboot.......but after it restarts....it doesnt reboot and it goes through same steps it has gone earlier asking me again whether i should go installing ubuntu along side windows.....etc...i have tried to do this 15 times...and same every time..


please help me....


thanks

---

### Post by ajgreeny on 2013-04-21
I have never used pendrivelinux so don't know its idiosyncrasies, if it has any, but I suggest you try booting to the live system rather than going straight to installation; that will let you see if there is a hardware problem or incompatibility that is causing your difficulties.

Are you also sure that the .iso file you used to make the USB is not faulty in any way; have you checked the md5sum of the image against the list at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) ?  If not, do so first, before spending more time trying to sort out the problem.

---

### Post by venkatamanne on 2013-04-21
> **ajgreeny said:**
> I have never used pendrivelinux so don't know its idiosyncrasies, if it has any, but I suggest you try booting to the live system rather than going straight to installation; that will let you see if there is a hardware problem or incompatibility that is causing your difficulties.

Are you also sure that the .iso file you used to make the USB is not faulty in any way; have you checked the md5sum of the image against the list at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) ?  If not, do so first, before spending more time trying to sort out the problem.



i checked it and the iso  file is proper......

i have an usb  that is booted(fat32)

and i set boot order 1 to usb...

plz help me with the steps....was trying to do this from a week

thanks

---

### Post by ibjsb4 on 2013-04-21
Did you do what ajgreeny suggested and use the option to try before installing?

And what version did you download?

---

### Post by venkatamanne on 2013-04-21
> **ibjsb4 said:**
> Did you do what ajgreeny suggested and use the option to try before installing?

And what version did you download?

i downloaded 12.10 desktop version....

i havent used that option to try before installing....

is it mandatory to try before??

---

### Post by ibjsb4 on 2013-04-21
> **venkatamanne said:**
> is it mandatory to try before??

Nope not mandatory, but a good way to see if its going to work at all.

---

### Post by Mark Phelps on 2013-04-21
If your intent is to do a dual-boot installation with Win7, then read the info below BEFORE you charge into that ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

