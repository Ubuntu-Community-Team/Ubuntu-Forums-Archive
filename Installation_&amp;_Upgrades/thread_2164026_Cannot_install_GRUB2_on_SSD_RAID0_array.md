---
title: "Cannot install GRUB2 on SSD RAID0 array"
date: 2013-07-20
forum: Installation &amp; Upgrades
---

### Post by maxxum on 2013-07-20
I had a working system, which got broken. I don't remember how I set this up last time. This is a jmicron RAID controller and two SSDs are in RAID0 / striped configuration. I have Windows 7 x64 on part of it and have been able to install Ubuntu 13.04 x64 via USB stick on the other partition. The installation "failed" with a grub error though I am pretty certain the problem is only bootloader. 
It would get into a grub rescue prompt which I had no experience with. With windows rescue mode I have for the moment, erased the MBR and am able to boot windows. I just want to put GRUB2 on it and see if the Ubuntu install boots. 

Booting form a Live USB, I have tried:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdf: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe36d922d

Disk /dev/sdf doesn't contain a valid partition table
fdisk: unable to seek on /dev/sde: Invalid argument
ubuntu@ubuntu:~$ ls -la /dev/mapper/
total 0
drwxr-xr-x  2 root root      180 Jul 20 12:37 .
drwxr-xr-x 16 root root     4540 Jul 20 12:38 ..
crw-------  1 root root  10, 236 Jul 20 12:38 control
brw-rw----  1 root disk 252,   0 Jul 20 12:37 jmicron_JRAID0_120g
lrwxrwxrwx  1 root root        7 Jul 20 12:38 jmicron_JRAID0_120g1 -> ../dm-1
lrwxrwxrwx  1 root root        7 Jul 20 12:38 jmicron_JRAID0_120g2 -> ../dm-2
lrwxrwxrwx  1 root root        7 Jul 20 12:38 jmicron_JRAID0_120g3 -> ../dm-3
lrwxrwxrwx  1 root root        7 Jul 20 12:38 jmicron_JRAID0_120g5 -> ../dm-4
lrwxrwxrwx  1 root root        7 Jul 20 12:38 jmicron_JRAID0_120g6 -> ../dm-5

ubuntu@ubuntu:~$ grub-install /dev/mapper/jmicron_JRAID0_120g
mkdir: cannot create directory ‘/boot/grub/i386-pc’: Permission denied

ubuntu@ubuntu:~$ sudo grub-install /dev/mapper/jmicron_JRAID0_120g
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

ubuntu@ubuntu:~$ sudo mount /dev/mapper/jmicron_JRAID0_120g /mnt
mount: /dev/mapper/jmicron_JRAID0_120g already mounted or /mnt busy
ubuntu@ubuntu:~$ 

```

Any help is greatly appreciated.

---

### Post by oldfred on 2013-07-20
I really do not know RAID, but with grub from a live installer, you have to first mount the drive and partition(s) with / (and /boot if separate) and then install grub.

Standard drive to install to MBR, you need to change to your RAID and install to its root.
to see partitions, You may need RAID driver from a live installer.
sudo parted -l
 sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

This is for "fakeRAID" but yours is jmicron
if RAID
For RAID reinstall from liveCD
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
"fakeRaid" with nVidia
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

Note in all BIOS install cases you are mounting the partition and installing to a root. (Unless UEFI).

---

### Post by maxxum on 2013-07-20
In my case, this is not a software raid, as you noted, it is BIOS based RAID controller (the so called fake raid) which is a part of the motherboard.
Further reading suggests that it might have been broken from 12.10 onwards. I used to have earlier version of Ubuntu which used to work well. It broke after upgrade and won't work with 13.04 either. 
One possibility is if I created a separate boot partition and later mount it and make it bootable.
Another possibility is to just use another hard drive for linux. This might be the least headache prone solution. :)

---

### Post by oldfred on 2013-07-20
If you install RIAD driver mdadm or dmraid driver(I do not know RAID to know which you need), then list partitions what does it show.
 sudo apt-get install mdadm

 sudo apt-get install dmraid

sudo parted -l

---

