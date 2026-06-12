---
title: "Unable to install Lubuntu in thumb drive using Startup Disk Creator"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by KayeNg on 2015-01-16
Hi guys.

If I look in GParted, my thumb drive is sdb, which has two partitions.
sdb1 stores all my data (spreadsheet, documents, mp3, pictures, etc.)
sdb2 is supposed to be my Lubuntu installation/startup disk.

sdb2 was formatted as fat32 because Startup Disk Creator doesn't seem to recognize ext2 or ext4; in other words, Startup Disk Creator doesn't list the sdb2 in "Device to use" if it's ext2 or ext4, so I formatted it as fat32

So I start the disk creator, all seems well, but towards the end an "Authentication" pop up message:  System policy prevents installing the bootloader.   It prompts me to enter my password.

I enter my password, then an "Installation failed" pop up message:  Failed to install the bootloader.

Anyone?
Thank you for your time.

---

### Post by sudodus on 2015-01-16
Which version of Ubuntu are you installing from, and which version are you installing to? The Startup Disk Creator has some problems with 14.10 when installed from older versions.

It has also problems when installing into a pendrive that is not empty. If it is important to keep the first partition and its data, maybe you can try using ***Unetbootin*** instead.

-o-

But I would not mess with a pendrive that is storing data (and I consider installing a bootable installer 'messing'). It is better to have a separate pendrive for booting. It can be reused many times. If you need no persistence (only use the live system and maybe install from it) a cheap and slow but reliable 4 GB Sandisk Cruzer Blade might do well. And in that case there are easier tools to make a USB boot drive for example ***mkusb***.

See this link and links from it [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Rex Bouwense on 2015-01-16
Do you want to install Lubuntu to the thumb drive or are you trying to create a start up disk? The procedures are a little different.

---

### Post by KayeNg on 2015-01-16
sudodus, I believe I'm installing to and from the same version, the latest version.  I've tried **Unetbootin** to install Lubunto when my thumb drive was completely empty, and it was successful.  So now I'm trying to install Lubuntu to a separate partition in the thumb drive, the other partition being a storage for my personal data files.

Rex, aren't they the same thing? I'm trying to make a LiveUSB in my thumb drive's second partition.  (the other partition contains my files)   I'm NOT trying to install Lubuntu in the thumb drive as I would in a hard disk.  Sorry, newbie here.

Anyway, this isn't really a pressing matter.  Thanks!!!

---

### Post by sudodus on 2015-01-16
> **KayeNg said:**
> sudodus, I believe I'm installing to and from the same version, the latest version.  I've tried **Unetbootin** to install Lubunto when my thumb drive was completely empty, and it was successful.  So now I'm trying to install Lubuntu to a separate partition in the thumb drive, the other partition being a storage for my personal data files.

Unetbootin lets you select which partition you want to use as target for the installation.

I just checked, there is a box where you can select another partition than what is pre-selected, click and get a menu to select from:

'Drive:' [and the box]

See the attached file, and please try it.

---

### Post by sudodus on 2015-01-16
Do you want to boot the pendrive from the second partition (only), or do you want a multi-boot pendrive, to boot from first, second, ... partition? In that case you need another tool.

---

### Post by C.S.Cameron on 2015-01-16
My understanding is that you can only do a Live or Persistent install to the first partition of a flash drive.
(I could be wrong).


Edit:
Live or Persistent

---

### Post by sudodus on 2015-01-17
If I remember correctly, the system in the following link boots a persistent live system from the second partition (/dev/sdb2)

[http://ubuntuforums.org/showthread.php?t=1885392&p=11546560#post11546560](http://ubuntuforums.org/showthread.php?t=1885392&p=11546560#post11546560)

```
ubuntu@ubuntu:~$ [COLOR=RoyalBlue]df[/COLOR]
Filesystem           1K-blocks      Used Available Use% Mounted on
/cow                   1808104     70412   1737692   4% /
udev                   1800780         4   1800776   1% /dev
tmpfs                   723244       852    722392   1% /run
[COLOR=#006400]/dev/sdb2              5234980   4885160    349820  94% /cdrom[/COLOR]
/dev/loop0              624512    624512         0 100% /rofs
tmpfs                  1808104        12   1808092   1% /tmp
none                      5120         0      5120   0% /run/lock
none                   1808104         0   1808104   0% /run/shm
/dev/sdb1              8794976   3601712   5193264  41% /media/USB-DATA
/dev/sr1                  6828      6828         0 100% /media/U3 System
```

---

### Post by KayeNg on 2015-01-18
Sudodus, yes, I want to boot the pendrive from the second partition (only). I'm going to try it now. Thanks guys!

---

