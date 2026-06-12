---
title: "Grub install problems"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by VEGO on 2007-04-21
Hi there,

I am new with Linux and Ubuntu...I have Fujitsu laptop and XP Home on it. I have made necessary partitions (ext2 and Linux-swap). I successfully download an image of Ubuntu and burned it on a CD. I boot it from CD and the Ubuntu comes up, no problems.. I do the install and on the very and of an installation process, I get message of grub installation failed, a fatal error. I don't get a message that installation is successful. If I reboot, I get the message no operating system found. My only choice is to boot from my Ubuntu CD. I can't boot windows any more as well. PLEASE HELP!!

---

### Post by bulldog on 2007-04-21
Perform the following command in a terminal```
sudo fdisk -l
``` it's a lowercase L not a one.
Put the output to the forum please.

---

### Post by VEGO on 2007-04-21
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5895    47351556   17  Hidden HPFS/NTFS
/dev/hda2   *        6154        7296     9181147+  f0  Linux/PA-RISC boot
/dev/hda3            5896        5929      273105   82  Linux swap / Solaris
/dev/hda4            5930        6153     1799280   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by bulldog on 2007-04-21
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 5895 47351556 17 Hidden HPFS/NTFS
/dev/hda2 * 6154 7296 9181147+ f0 Linux/PA-RISC boot
/dev/hda3 5896 5929 273105 82 Linux swap / Solaris
/dev/hda4 5930 6153 1799280 83 Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$
```
Can you explain to me what is the hda2 partition?

---

### Post by VEGO on 2007-04-21
That is the partition I created for Ubunta as a second operating system

---

### Post by bulldog on 2007-04-21
And what about hda4 then?
It seems a little odd to me how hda2 is listed.
Can't make out what it is anyway.:(

---

