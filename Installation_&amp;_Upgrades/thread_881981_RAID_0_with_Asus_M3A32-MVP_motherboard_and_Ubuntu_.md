---
title: "RAID 0 with Asus M3A32-MVP motherboard and Ubuntu Hardy x64"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by pgil on 2008-08-06
Hi!
I'm trying to install Hardy 8.04 x64 on a new system in RAID 0.
After installing, Ubuntu doesn't boot, I think it could be a problem with "dmraid".
To continue, I show my PC's configuration and the steps I've followed.

_**Hardware**_
Asus M3A32-MVP Deluxe motherboard 
AMD Phenon 9550 CPU
2 HD x 400 GB Maxtor in RAID 0 

_**Considerations**_
The mobo has two RAID controllers, a Marvell 6121 and a SB600 (chipset AMD 790FX). The Marvell is disabled by BIOS and the SB600 is in use with a RAID 0 and six partitions:
Primary, NTFS
Primary, NTFS
Secondary, ext3
Secondary, reiserfs
Secondary, swap
Secondary, NTFS

_**Steps**_
I boot from Ubuntu x64 CD, and I try to install the system following the instructions of FakeRaidHowto
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
The first problem becomes when I try to install the “dmraid” package on the live CD session:

```
sudo apt-get install dmraid 

sudo dmraid -ay

/dev/sda: "ddf1" and "nvidia" formats discovered (using ddf1)!
/dev/sda: "pdc" and "ddf1" formats discovered (using ddf1)!
/dev/sdb: "ddf1" and "nvidia" formats discovered (using ddf1)!
/dev/sdb: "pdc" and "ddf1" formats discovered (using ddf1)!

ls /dev/mapper/

control
ddf1_xxxxxxxxx
```

It seems like if the raid controller doesn’t found the partitions, so I try to force it:

```
sudo dmraid -an

sudo dmraid -ay -f nvidia -v

ls -l /dev/mapper
control
nvidia_xxxx
nvidia_xxx1 
nvidia_xxx2 
nvidia_xxx5 
nvidia_xxx6 
nvidia_xxx7 
nvidia_xxx8 
```

OK, It works, so I continue the installation without problems. I install “dmraid” package into the /target environment and I change the /etc/init.d script to force it to load “nvidia”:


```
sudo chroot /target
apt-get install dmraid
nano /etc/init.d/dmraid
```

I modify the lines that contain...

```
dmraid --active yes --verbose
```

adding...

```
dmraid --active yes --verbose --format nvidia
```

I install grub and reboot the new installed system.

Grub loads fine, and when I select the "Ubuntu, kernel 2.6.20..." boot option, the "kernel alive..." message appears and also the splash screen, and it seems like if the OS started to load, but a few minutes later the splash screen disappears and a command line shows a message like this:

```
Busybox
check root= bootarg cat /proc/cmdline or missing modules, device : cat /prc/modules ls /dev 
ALERT! /dev/mapper/ /dev/mapper/ nvidia_xxxx6 does not exist. Dropping to shell
```


[SIZE="3"]**What can I do? Please, help.**[/SIZE]

---

