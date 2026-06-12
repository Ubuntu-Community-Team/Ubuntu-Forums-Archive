---
title: "HELP--No valid drive after installing Ubuntu-Grub Failed"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by JC-TC on 2010-02-01
I installed unbuntu 9.10 on a dual partition for alongside windows.  Grub failed during installation and now I can not boot to windows or ubuntu.  I can not repair with the windows cd, I can not do anything in Windows recovery no format, no fixboot, no chkdsk, no anything, it tells me there is no valid drive when I am in dir C:.  In Ubuntu live CD I can see all the files  are there on the local disk.  What do I need to do to fix this.

Sorry for dual post but I can not find the post I just posted!

---

### Post by dabl on 2010-02-01
You're probably going to have to install Grub (again):

[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

This could be done with the Live CD, or possibly a Super Grub CD.

---

### Post by JC-TC on 2010-02-01
I am sorry but this is way over my head, is there another way to do this?

---

### Post by darkod on 2010-02-01
Don't worry, it's quite simple and it only takes two commands. Boot with the ubuntu 9.10 cd, Try Ubuntu option, and follow the instructions for 9.10 from here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you are still confused after reading that, just execute in terminal:
sudo fdisk -l

and post the result here, I'll give you the exact commands you need to enter for your case.

---

### Post by JC-TC on 2010-02-01
OK I just got back from discount electronics and cpu is booting now. I am using my phone. Are you still around for help I hope.

---

### Post by JC-TC on 2010-02-01
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


OK Now what??

---

### Post by RTrev on 2010-02-01
> **JC-TC said:**
> 
ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'


Looks to me like you used a numeric 1 (one) instead of an alpha lowercase L ("el").  L as in List. ;)

---

### Post by JC-TC on 2010-02-01
ok trying that now

---

### Post by JC-TC on 2010-02-01
this is what it returned

Unable to read /dev/sda
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

It seems there is no valid drive no even though I can see the files on it?

---

### Post by darkod on 2010-02-02
> **JC-TC said:**
> this is what it returned

Unable to read /dev/sda
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

It seems there is no valid drive no even though I can see the files on it?

Uhhh, if it doesn't even show the drive as valid, I'm not sure what to do. There is a package called TestDisk that allows to check the disk and even recover partitions, but I don't know enough about it to instruct you what to do with it.

I hope someone else can jump in.

---

### Post by RTrev on 2010-02-02
For what it's worth, I've had nothing but headaches with grub after Karmic came out.

I used to use two small drives for boot disks, and it was a simple matter to keep two distros, allowing one per disk and telling the distro to take the entire disk and have its way with it.

The first time I installed Karmic, it looked okay, saying it had found this one other operating system and that installation had succeeded.  And then neither distro would boot.  Ever since Grub-2 I have yet to be able to get two distros to install without blowing away everything.  It's reached the point that I've given up, and don't plan to even test Lucid until it's been out for a couple weeks or so.  I used to love checking out the alphas.

So... I can't say I'm surprised to hear the problems the OP is having! :icon_frown:

---

