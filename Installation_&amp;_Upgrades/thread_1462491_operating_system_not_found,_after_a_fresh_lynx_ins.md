---
title: "operating system not found, after a fresh lynx install"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by gioby on 2010-04-25
people, I have the feeling that Windows 7 someway mess up with grub2, making the system inaccessible after a fresh install. This is the second time I had a problem with installing lynx on a new computer, after trying it on two different computers.


I wanted to install today's daily build (April 25th) of Lucid Lynx on my laptop, a DELL (tomorrow I will post you the model's name).

Since I was having problems to make the computer start from CD, I used the WUBI's "Help me run Linux from CD" option to install a "Launch from CD" option to WIndows 7's boot.

Then, I rebooted, and I was able to install Ubuntu in a separate partition, without getting any error.
After the first reboot with linux installed, I started WIndows 7 first, which made a file system check, and then rebooted by itself.
After this reboot, my system didn't boot any operating system. This was the only message on the screen:

"""
no module name found
Aborted. Press any key to exit.   (I pressed a key)
Broadcom UNDI PXE-2.1 v11.0.9
Copyright (C) 2000-2008 Broadcom Corporation
Copyright (C) 1997-2000 Intel Corporation
All rights reserved.
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Broadcom PXE ROM.
Operating System not found
"""

Now, I have managed to boot the computer from the CD, so I can access it and give you all the log information you want, but I am going to try a reinstall soon.
I have also tried to chroot in the installed ubuntu system and make an update-grub, but I was getting a '/dev partition not found' error.

---

### Post by garvinrick4 on 2010-04-25
> **gioby said:**
> people, I have the feeling that Windows 7 someway mess up with grub2, making the system inaccessible after a fresh install. This is the second time I had a problem with installing lynx on a new computer, after trying it on two different computers.


I wanted to install today's daily build (April 25th) of Lucid Lynx on my laptop, a DELL (tomorrow I will post you the model's name).

Since I was having problems to make the computer start from CD, I used the WUBI's "Help me run Linux from CD" option to install a "Launch from CD" option to WIndows 7's boot.

Then, I rebooted, and I was able to install Ubuntu in a separate partition, without getting any error.
After the first reboot with linux installed, I started WIndows 7 first, which made a file system check, and then rebooted by itself.
After this reboot, my system didn't boot any operating system. This was the only message on the screen:

"""
no module name found
Aborted. Press any key to exit.   (I pressed a key)
Broadcom UNDI PXE-2.1 v11.0.9
Copyright (C) 2000-2008 Broadcom Corporation
Copyright (C) 1997-2000 Intel Corporation
All rights reserved.
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Broadcom PXE ROM.
Operating System not found
"""

Now, I have managed to boot the computer from the CD, so I can access it and give you all the log information you want, but I am going to try a reinstall soon.
I have also tried to chroot in the installed ubuntu system and make an update-grub, but I was getting a '/dev partition not found' error. Go into Windows install and go to C: drive and look rught nest to Users for Ubuntu and open that folder and select uninstall. That will get rid of WUBI install and the wubi out of windows "bededit" its boot manager. 

 Now take your Ubuntu disk put it in tray and restart computer. When the it comes up pick to install, then just focus and read the entrys on each page. There are 3 choices to let the disk pick your install, to wipe out whole disk and install Ubuntu or to do it manual.
For you use the first to let the disk pick out the install. Do not worry if you want it larger or smaller it can be done later. This is the best way for a first timer. It will give you a /root partition and a swap partition and put the grub2 in the right place. You will now have a small partition called sda1 that is called system, that is your boot. A sda2 that is large that is your Windows 7 and a sda4 usually that is Recovery for Windows 7 (do not worry that Ubuntu reads it as Vista it is a Windows goof up.)  sda3 is going to be a extended partition that inside of that will exist your Linux and swap. Anymore linux OS's you want to install will go right inside of that sda3 extended partition. 
sda1, sda2,sda3 and so forth is how linux reads a drive. Windows calls it C,D,E,F J and so on. From now on your drive is sda and your partitions are sda1, sda2 and so on. Forget about C,D,E and such.
 In a program called gparted we can increase or decrease size of partition until you learn to do it manually. "gparted is a partition editor that can do everything but kiss you good night and is one package you want to learn how to use. Ok get started.
  Oh by the way Lucid WUBI install is still in Beta and testing so if it screwed up it could very well be WUBI install itself. WUBI is a folder inside of Windows and a partition of its
own is so much better than WUBI anyway. I have done both so believe me there.

---

### Post by gioby on 2010-04-25
Thank you very much for the answer: however, I think you didn't read my question properly. I was saying that I received the error message I posted here after doing a fresh install. Moreover, I can't boot any operating system, so I can't enter or execute programs in the windows installation. By the way, I have been using Linux for quite many years now, so I know how to install it :-)

I have reinstalled Lynx on the same computer, and rebooted. This time I could run Ubuntu first and it was running fine, but after the first time I loaded Windows 7, and then rebooted again, the error message returned again.

I have the feeling that the Windows 7 loader is someway responsible for this, as if it tries to repare the boot loader and therefore mess up grub. I was wondering if someone can confirm me this behaviour, and then I will post a bug report.

---

### Post by gioby on 2010-04-25
Thank you very much for the answer: however, I think you didn't read my question properly. I was saying that I received the error message I posted here after doing a fresh install. Moreover, I can't boot any operating system, so I can't enter or execute programs in the windows installation. By the way, I have been using Linux for quite many years now, so I know how to install it :-)

I have reinstalled Lynx on the same computer, and rebooted. This time I could run Ubuntu first and it was running fine, but after the first time I loaded Windows 7, and then rebooted again, the error message returned again.

I have the feeling that the Windows 7 loader is someway responsible for this, as if it tries to repare the boot loader and therefore mess up grub. I was wondering if someone can confirm me this behaviour, and then I will post a bug report.

---

### Post by garvinrick4 on 2010-04-26
As you have said you do no your way around Linux, are you running WUBI or a partiiton.

So your sudo fdisk -l shows a sdaX for your linux partition yet when running a Live Cd
you cannot mount a /dev/sdaX.

Here is mine:
rick@rick-laptop:~$ sudo fdisk -l
[sudo] password for rick: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7e8e0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       15985   128192511    7  HPFS/NTFS
/dev/sda3           15985       36006   160819192+   5  Extended
/dev/sda4           36007       38913    23350477+   7  HPFS/NTFS
/dev/sda5           21349       22807    11719417+  83  Linux
/dev/sda6           15986       17387    11261533+  83  Linux
/dev/sda7           17388       21348    31816701   83  Linux

Partition table entries are not in disk order

Now a sudo blikid
rick@rick-laptop:~$ sudo blkid
/dev/sda1: LABEL="SYSTEM" UUID="C6EECCF3EECCDCB5" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="66B0BDBFB0BD95D1" TYPE="ntfs" 
/dev/sda4: LABEL="RECOVERY" UUID="524C43ED4C43CB05" TYPE="ntfs" 
/dev/sda5: LABEL="maverick" UUID="b2386000-aba8-49c2-b59b-7c2b87b37316" TYPE="ext4" 
/dev/sda6: LABEL="lucid" UUID="c4c94121-65f4-40a3-8ce3-80c720438f6b" TYPE="ext4" 
/dev/sda7: LABEL="home" UUID="1adc1fb7-dd51-48e9-8fea-77d6c6a75e78" TYPE="ext4" 
rick@rick-laptop:~$ 

So in Live CD I run Code:

sudo mkdir /media/lucid
sudo mount /dev/sda6 /media/lucid
sudo chroot /media/lucid

And I am now in root for my lucid labeled partition.
Why does yours say /dev partition not found? If there is one. Makes no sense. If there is a linux partition it will mount. What does your fdisk -l and blkid say?

---

### Post by gioby on 2010-04-26
ok, I solved it, it was this bug:
- [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/482757](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/482757)

---

### Post by ankit.jivrani on 2010-07-03
I have dell laptop with windows professional n then i installed ubuntu 9.10.
Actually i have same problem that i get same error that 

Grub loading.
The symbol ' ' not found.
Aborted. Press any key...

i have tried the solution which is provided but still i get problem. i also tried link which is provided in solution..

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/482757](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/482757)

so what should i do???
provide some solution...

---

