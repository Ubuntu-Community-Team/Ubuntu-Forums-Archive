---
title: "Help! QTparted crashes on kubuntu install"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by trawler on 2007-01-08
2 days ago i rebooted my comp, and kubuntu wouldn't boot up.
"A good change to freshen things up" i thought - and so I decided to re-install kubuntu edgy from scratch.
And boy what a mistake that was!
I've been struggling with this for 2 days now, and i'm deeply disappointed.
I've downloaded kubuntu edgy, and tried running the installer, but whenever it gets to the partitioning phase (phase 5), qtparted crashes with these errors:
```
No Implementation: Support for opening ntfs file systems is not implemented yet.
```

Since i have windows set up on the same hard-drive, i can't really format the whole thing, but i have to keep my ntfs partitions (and this is an excellent example of why i do).
I've tried using the new "feisty" live cd, hoping the bug was fixed there, but the outcome is even worse there - when it gets to the partitioning phase, kde just freezes completely... ](*,) 

I've already found a bug that was posted [https://launchpad.net/ubuntu/+source/qtparted/+bug/59819]("https://launchpad.net/ubuntu/+source/qtparted/+bug/59819"), but apparently nothing was being done about it yet.

I haven't used the kubuntu edgy live cd before, since i used apt to upgrade from dapper drake. 

Does anyone know how to work-around this problem?? It's getting extremely frustrating, and i miss my desktop... :cry:

---

### Post by kebes on 2007-01-08
One option would be to do a Dapper install (and then upgrade like you did before). I wouldn't recommend using Feisty--it's brand new and very unstable (not meant for daily use).

During the installation, does it crash only when you try to assign your NTFS a mount point? Perhaps try not mounting it anywhere, and see if installation proceeds. (Once fully installed you can of course mount the drive if you need it.)


Also, I'm assuming you didn't mount the NTFS disk, right? (That would probably crash parted.) Maybe double-check that it's not mounted before starting the installer from the LiveCD session.

---

### Post by smurphy on 2007-01-24
Actually - having the same issue here.
qparted crashes when it scans the local harddisk (sda - S-ATA). All I get is this:

No Implementation: Support for opening ntfs file systems is not implemented yet.
Error: File system has an incompatible feature enabled.

and no possibility to install it on my Box.
Note that this is my Gaming Box - and as I use a Modell-Airplane Simulator to connect to my radio-control - I need windows. Aerofly does not run under Linux. That box mostly runs under LInux - in Summer. Winter - loads of Simulator runs :).
I have not even the chance to go into manual mode. All modes fail.
Note that this beheaviour occures with Kubuntu 6.06/6.06.1 and LTS, 6.10 and feisty rc2.
I managed to get all other RPM based systems to install without a issue (RedHat/Suse) - but all Debian based systems do fail on the S-ATA setup.
Motherboard - Asus A7N8X - Athlon XP2800+, 1GB Ram with a Nvidia GT6000 128MB Card.
160GB S-ATA.
```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)

```
Can provide you informations on the Disk - as hdparm strikes on S-ATA disks under kubuntu... :)
```

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+   7  HPFS/NTFS
/dev/sda2             609        1200     4755240   83  Linux
/dev/sda3            1201        1340     1124550   82  Linux swap / Solaris
/dev/sda4            1341       19929   149316142+   5  Extended
/dev/sda5            1341       10628    74605828+   7  HPFS/NTFS
/dev/sda6           10629       19929    74710251   83  Linux

```

Any hint ? I'd love to have the possibility to just use fdisk to define  my partitions ...

---

### Post by kebes on 2007-01-24
Hi smurphy,

Things to try:

1. Use the Alternate CD instead of the Desktop install (LiveCD). This often fixes bugs like this. Plus it uses the commandline partition editor, so it might work.

2. Install using the Ubuntu CD (NOT the Kubuntu one). The reason for this is that during the install it will use "gparted" instead of "qtparted". This might fix the problem. Don't worry, once Ubuntu is installed you can do "sudo aptitude install kubuntu-desktop" and you'll have a normal Kubuntu system.

3. After booting into the LiveCD or a console in the Alternate CD, you could manually use the commandline "parted" instead of the graphical qtparted or gparted. After setting up your partitions properly you could run the install but skip the partition step (since it's already set up properly).


Hope that helps.

---

### Post by smurphy on 2007-02-16
Using the alternate installer with Text-Mode made no problems ...
So all of you know :) Thx for the hint.

---

