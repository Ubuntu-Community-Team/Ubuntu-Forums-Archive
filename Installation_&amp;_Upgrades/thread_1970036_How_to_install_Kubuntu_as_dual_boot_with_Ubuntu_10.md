---
title: "How to install Kubuntu as dual boot with Ubuntu 10.o4"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by Bumpalot on 2012-04-30
Am at a loss as to installing Kubuntu 12.04 as dual boot with Ubuntu 10.04. Have attempted it several times & end up with the original Ubuntu install. After web searching I find little or no info on this topic. Maybe someone can suggest sources. Am using amd64 bit processor, 500G drive NVidia GTX 550 Ti processor, 8G ram. Sure could use some constructive help, which seems lacking re KDE net sources.

---

### Post by tommcd on 2012-04-30
> **Bumpalot said:**
> Am at a loss as to installing Kubuntu 12.04 as dual boot with Ubuntu 10.04. ...
If you would simply like the option to login to Ubuntu with Gnome/Unity, or to login to KDE when you boot the computer, then you can add KDE to your Ubuntu install. Just install the *kubuntu-desktop* package to Ubuntu. Then reboot and you should be given the option to login to KDE or Gnome or Unity, or whatever you are using on Ubuntu 10.04. See this: [http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)


If you want to actually dual boot Ubuntu on one partition and Kubuntu on another partition, then install Ubuntu first, and allow Ubuntu's grub to install to the MBR.
Then install Kubuntu to another hard drive or partition. DO NOT install Kubntu's grub to the MBR. Install Kubuntu's grub to the Kubuntu root partition, or whatever.
Then just boot into Ubuntu and open a terminal and run: ```
sudo update-grub
```
and your Kubuntu install should be added to Ubuntu's grub menu when you boot the computer and give you the option to boot either Ubuntu or Kubuntu.

If your computer has very recent hardware, then it is possible that some of your hardware is not supported by the default kernel that is in Ubuntu 10.04, since 10.04 is getting a bit old.
It may be better to dual boot Ubuntu 12.04 with Kubuntu 12.04 if a dual boot system with Ubuntu and Kubuntu is really what you want.

---

### Post by Bumpalot on 2012-05-01
Thanks for your previous suggestions!
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Attempt at dual booting Ubuntu 10.4 (orig install) with kubuntu 12.04 (new install)
Used DParted to create sdb1 -> sdb8

Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cc0f2
My objective is to have Ubuntu 10.4 & Kubuntu on the same drive.
If I have problems with Kubuntu I can always get back to Ubuntu & solve what's needed. I want Kubuntu to be my main concern.
Ubuntu is running fine on my very recent hardware (5 months old).

Terminal extract:
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        9961       11266    10490445   83  Linux     Ubuntu 10.4
/dev/sdb2               1        9960    80000001    5  Extended  *          *
/dev/sdb3           11267       17862    52982370   83  Linux     *          *
/dev/sdb4           17863       31281   107788117+  83  Linux     ************
/dev/sdb5               1        1245     9999360   83  Linux     Kubuntu 12.04
/dev/sdb6            1246        3735    19998720   83  Linux     *           *
/dev/sdb7            3736        8714    39993786   83  Linux     *************
/dev/sdb8            8715        9960     9999360   82  Linux swap / Solaris

Partition table entries are not in disk order <<<<< see my note below

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20b4b959

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS
bump@bumpyputer:~$ 
QUESTIONS:
Can only boot to Ubuntu. How can I change grub to get a dual boot?
How can I correct this? - edit the MBR? Edit Kubuntu grub? or both?
RE: Partition table entries are not in disk order.
Thanks for keeping suggestions simple as I am a newbie!
I wanted to insert a graphic here but can't figure out how to do it!

---

### Post by tommcd on 2012-05-01
How did you install Kubuntu? When it came to the part of the Kubuntu install where you install the grub boot loader *what specifically did you do with grub*?

Depending on where you installed Kubuntu's grub, either Ubuntu 10.04 or Kubuntu 12.04 controlls the MBR. In either case you should be able to boot Ubuntu (or possibly Kubuntu) and just run:
```
sudo update-grub
``` and the other OS would be added to your gryb options when you boot.

You could try using a **boot-repair** CD to set this up for you. See this: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bumpalot on 2012-05-23
This thread is closed. Had so much trouble with the above, reformatted the drive & installed only kubuntu 12.04. I found it to be so  full of bugs,  I wiped the drive & installed Ubuntu 12.04. Am having lots of trouble with that too - but will start a new post for that.
Thanks for your help guys!

---

### Post by syntax3rror on 2012-09-17
hmm,,  I looking for this kind of installation too.. But sounds like there were no solution given.. :(

---

