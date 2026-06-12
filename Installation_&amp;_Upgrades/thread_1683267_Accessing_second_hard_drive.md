---
title: "Accessing second hard drive"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by JonCox on 2011-02-07
Hi,

So I recently installed Ubuntu 10.10 64-bit on my computer.

I installed it on my 60gb SSD hard drive, and in the installation it never acknowledged the existence of my second hard drive.

The hard drive that I keep all my files on, and which I want to make my home folder if I can, is a Western Digital Caviar Black 1TB SATA 6Gb/s 64MB cache (WD1002FAEX).

I've read the following: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount) but honestly cannot work out how to access the hard drive from my Ubuntu installation. 

I did have Windows 7 64-bit prior to installing Ubuntu. I have backed up all the files on the hard drive, but if I could just access them straight off that would be super cool.


Does anyone know how I can use the second hard drive?


Thank you for your help :)


EDIT:
The following directories are currently in my /dev/ folder:
ati/
block/
bsg/
bus/
char/
cpu/
disk/
input/
mapper/
net/
pktcdvd/
pts/
shm/
snd/
usb/

---

### Post by oldfred on 2011-02-07
Any partition you want to permanently access you should add to fstab.

If you want your /home then it is easier as part of the install but you can follow the move /home, but if you have made settings in your current /home then you have to merge those before changing to another /home.

If you just want to mount /data and it has Music, Documents etc folders, you can link those into /home in place of your current default folders. (make sure defaults are empty before deleting & linking in new).

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Post this:

```
sudo fdisk -lu
sudo blkid
```

---

### Post by JonCox on 2011-02-07
> **oldfred said:**
> Any partition you want to permanently access you should add to fstab.

If you want your /home then it is easier as part of the install but you can follow the move /home, but if you have made settings in your current /home then you have to merge those before changing to another /home.

If you just want to mount /data and it has Music, Documents etc folders, you can link those into /home in place of your current default folders. (make sure defaults are empty before deleting & linking in new).

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Post this:

```
sudo fdisk -lu
sudo blkid
```

>sudo fdisk -lu
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d2dfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   112351231    56174592   83  Linux
/dev/sda2       112353278   117229567     2438145    5  Extended
/dev/sda5       112353280   117229567     2438144   82  Linux swap / Solaris



> sudo blkid
/dev/sda1: UUID="aca02bba-c1d7-489b-a68f-26c1e81ed6bb" TYPE="ext4" 
/dev/sda5: UUID="a30dba99-dc92-4e7d-92d6-404aeeab3d8e" TYPE="swap"


Any idea what's going on?

---

### Post by oldfred on 2011-02-07
They are not showing any second drive?

Does BIOS see drive? Connections are good?

---

### Post by JonCox on 2011-02-07
> **oldfred said:**
> They are not showing any second drive?

Does BIOS see drive? Connections are good?

I've made the assumption all the connections are good, as I was able to access the files fine this morning when Windows 7 was installed.

I checked BIOS, it looks like it isn't detecting the hard drive automatically. (Although in the boot section it does recognize it as the 2nd Drive to boot from weirdly.)

As I haven't knocked it or anything since this morning when the hard drive worked perfectly with Windows 7 - what do you think I've done so that it is now not recognized by the BIOS?


The motherboard is an Asus P6X58D-E Intel X58 (Socket 1366) DDR3.

(It would be very annoying at this point to have to go back to Windows after spending the whole day trying to fix this.)


Thank you very much for your help though :)

---

### Post by JonCox on 2011-02-07
It looks like 6 Gb/s ports don't work with Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1614764](http://ubuntuforums.org/showthread.php?t=1614764)

[http://ubuntuforums.org/showthread.php?t=1513174](http://ubuntuforums.org/showthread.php?t=1513174)

Excellent explanation given here:
[http://furiouspurpose.me/2010/12/27/the-new-sata-6-gbs-hardware-on-ubuntu-linux/](http://furiouspurpose.me/2010/12/27/the-new-sata-6-gbs-hardware-on-ubuntu-linux/)


I could simply open up my computer and move the 2nd hdd from a 6Gb/s to 3Gb/s port. I slightly resent having to resort to doing that though.

I may just go back to Windows 7 where everything just works for me - and continue running Ubuntu in a VM for all my work.

Looks like I've wasted a lot of time :(

---

### Post by djeikyb on 2011-02-08
I posted an answer at AskUbuntu. Basically, the problem is specifically the kernel you're using. Upgrade the kernel, problem solved. Do this manually by downloading the latest kernel source, or install a third party ppa.

[http://kernel.org/](http://kernel.org/)
[http://www.ubuntuupdates.org/ppa/kernel-ppa](http://www.ubuntuupdates.org/ppa/kernel-ppa)
[http://askubuntu.com/questions/25168/accessing-second-hard-drive/25247](http://askubuntu.com/questions/25168/accessing-second-hard-drive/25247)

---

