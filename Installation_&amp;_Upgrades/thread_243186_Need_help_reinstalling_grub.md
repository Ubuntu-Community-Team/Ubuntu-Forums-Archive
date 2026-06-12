---
title: "Need help reinstalling grub"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by randell6564 on 2006-08-24
Hey folks!

Well, I am running ubuntu dapper on Hda1.  I also have a 20GB Ide (Hdb1) that I WAS using just for storage.

I decided to dual boot, using Ubuntu and Ubuntu C.E.

I installed Ubuntu Christian Edition onto Hdb1, but was not able to reboot.

I did not get an option to install grub to the MBR from the Christian Edition, so now I'm stuck!

I Am here only because I booted off the ubuntu C.E. cd.

Can someone please give me the instructions on how to reinstall grub to the MBR?

Here is my fdisk -l.,

[B]scott@bigboss:~$ sudo fdisk -l
Password:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14759   118551636   83  Linux
/dev/hda2           14760       14946     1502077+   5  Extended
/dev/hda5           14760       14946     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2377    19093221   83  Linux
/dev/hdb2            2378        2482      843412+   5  Extended
/dev/hdb5            2378        2482      843381   82  Linux swap / Solaris
[/B]

Thanks Guy's!

---

### Post by cleentrax on 2006-08-24
Didn't help me,  but maybe it will help you:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by randell6564 on 2006-08-24
> **cleentrax said:**
> Didn't help me,  but maybe it will help you:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks my friend!  I'm off to try it!

Funny thing is.,I LIKE this setup that I have right now!  Each time that I want to boot, I have to use the Ubuntu Christian Edition CD, to select the OS that I want!

If I just boot without the cd, I get nothing!  By using the CD, I can choose to boot to Dapper or the Christian Edition!

Pretty secure I'd say!  Nobody but me can boot my box!

I like it ,but I still want to get the boot loader reinstalled to the MBR.

So, Thanks Again!

---

### Post by randell6564 on 2006-08-24
> **cleentrax said:**
> Didn't help me,  but maybe it will help you:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

It's all greek to me too!  What the hell good is the manual if a newb can't understand it?

I know.,Flame Away!  I can take it!  I JUST want to reinstall grub to my MBR!  How would I go about doing that with two WORKING OS's?
(they both work, but I cant boot to them without using the CD)

---

