---
title: "Installer freezes when loading the partitioner"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by Beige on 2008-01-30
I can succesfully get to the part of the installer where it would normally load up the partitioner, but on this particular computer it's totally freezes up, i'm left with a frozen desktop on the live cds or a blank blue screen with a grey bar at the bottom on the alt cds,

I've tried most variation of ubuntu except kubuntu and all fail at the same point.


Debian etch however installs and functions just fine


I can't remember the exact specs of the machine, but it goes something like this:

AMD 3800X2
NVidia based mobo
2Gb ram
7800GT 256Mb
SATA 250Gb HDD (WinXP)
IDE 80Gb (Linux, eventually...)

Can't think of anything else of consequence :)



***EDIT***

Oh yeah, worth mentioning, i've been playing about with Linux for some years, so i'm not a complete novice, just this one has me stumped

---

### Post by taurus on 2008-01-30
Are you using the Gutsy LiveCD version?  Have you tried giving the alternate CD a shoot?

---

### Post by Beige on 2008-01-30
I've tried both Live CD and the Alt CD, both freeze up at the same point, where the partitioner is loaded, at least i assume thats where it's crashing, perhaps it's actually when it's scanning for drives?

---

### Post by taurus on 2008-01-30
Back to the LiveCD.  Before you click on the install icon, can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Beige on 2008-01-30
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47534752

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9402    75521533+  83  Linux
/dev/hda2            9403        9732     2650725    5  Extended
/dev/hda5            9403        9732     2650693+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb537b537

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29764   239079298+   7  HPFS/NTFS
/dev/sda2           29765       30401     5116702+   f  W95 Ext'd (LBA)
/dev/sda5           29765       30401     5116671    b  W95 FAT32
ubuntu@ubuntu:~$ 


```


hda currently has Debian installed, sda has WinXP

---

### Post by Beige on 2008-01-30
Booted off an old 6.06 cd and i get the lines in the picture looping each only slightly different, since it says ata a few times, i wander if it's related?

[IMG]http://www.beigematchbox.co.uk/forums/ubuntu/606.jpg[/IMG]

I left it running for 5mins or so before i rebooted

---

### Post by Beige on 2008-01-30
More experiments,

Booted up a Linux Mint live cd and ran the installer, which looks to be the same one used in Ubuntu and it crashes in exactly the same place

---

