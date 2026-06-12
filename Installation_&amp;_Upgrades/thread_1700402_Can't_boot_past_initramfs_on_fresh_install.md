---
title: "Can't boot past initramfs on fresh install"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by samagon on 2011-03-05
Howdy guys. Let me preface this by admitting that i am a total linux noob. 

I have a Toshiba NB205 netbook ([FONT=Arial]1.66 GHz Intel Atom N280/ 160GB 5400RPM SATA drive/ Intel Graphics Media Accelerator GMA950/ 2GB Ram 800 MHz[/FONT]) that came preloaded with XP. I downloaded the latest Ubuntu Netbook Edition and used Universal-USB-Installer-1.8.3.4 (for windows) to make a live USB stick. I booted the live version of Ubuntu Netbook and from there i installed it to my HDD choosing to overwrite my Windows partition. The problem is that after i installed it i can't boot into the OS. I get the following message:

[FONT=Arial] Gave up waiting for root device. Common Problems:
- Boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/7bf50e45-7867-4dd6-86df-6d674181dca1 does not exist. Dropping to shell![/FONT]

If anyone could shed some light on this I'd really appreciate it. Thanks in advance.

---

### Post by Hedgehog1 on 2011-03-05
samagon,

Please boot off your USB stick (you may be posting from it right now). :D

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge...***

:KS

---

### Post by samagon on 2011-03-05
Disk /dev/sda: 8021 MB, 8021606400 bytes
5 heads, 32 sectors/track, 97920 cylinders
Units = cylinders of 160 *  512 = 81920 bytes
Sector size (logical/physical): 512 bytes / 512  bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk  identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1    *          51       97920     7829568    b  W95 FAT32

Disk  /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track,  19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size  (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal):  512 bytes / 512 bytes
Disk identifier: 0x000853ec

   Device  Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18693   150145024   83  Linux
/dev/sdb2            18693       19458     6142977    5  Extended
/dev/sdb5            18693       19458     6142976   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by wilee-nilee on 2011-03-05
> **samagon said:**
> Disk /dev/sda: 8021 MB, 8021606400 bytes
5 heads, 32 sectors/track, 97920 cylinders
Units = cylinders of 160 *  512 = 81920 bytes
Sector size (logical/physical): 512 bytes / 512  bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk  identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1    *          51       97920     7829568    b  W95 FAT32

Disk  /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track,  19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size  (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal):  512 bytes / 512 bytes
Disk identifier: 0x000853ec

   Device  Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18693   150145024   83  Linux
/dev/sdb2            18693       19458     6142977    5  Extended
/dev/sdb5            18693       19458     6142976   82  Linux swap / Solaris
ubuntu@ubuntu:~$

So I think the install put grub on the thumb which registers as sda so from gthe thumb run the fdisk -l command to confirm this and if the 160 hd is still showing as sdb run these two commands.
```
sudo mount /dev/sdb1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sdb
```
reboot to the install and run
```
sudo update-grub
```
Here is the link to the commands.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

When you boot with a thumb sometimes the thumb is listed as the first hard drive in this case sda

---

### Post by samagon on 2011-03-06
I get to the last step, but after i type the command i get

```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev  mounted?).
```

---

### Post by wilee-nilee on 2011-03-06
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Personally since this is a fresh install I would have just reinstalled but I'm familiar with partitioning and using Linux.

---

