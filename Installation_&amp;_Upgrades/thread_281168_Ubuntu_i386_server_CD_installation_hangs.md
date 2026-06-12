---
title: "Ubuntu i386 server CD installation hangs"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by forfox on 2006-10-20
Hey there! :)

I recently built a new box out of spare bits with the intention of setting it up as a LAMP server for development use / playing with. I downloaded the i386 server ISO (6.06), burnt it and began installing. The installer got to 76% complete ("retrieving and installing kernel") and then froze. The MD5 hash of the downloaded ISO was correct and the "check for defects" utility didn't find any problems with the CD. Just to make sure, I downloaded another server ISO from a different mirror site, burnt that, and still got the same problem during install at the same place. Again, no problems with the ISO or the CD.

The install freezes at this point on both the LAMP and basic server installations.

Oddly, I *can* install Ubuntu from the i386 desktop ISO on the same system with no problems (although obviously this installs a lot of stuff I don't want/need). It detects my hardware and network just fine, so I guess it can't be an issue with the PC being not compatible with Ubuntu...

System specs:
AMD Duron 800MHz
256MB RAM
Onboard LAN/sound
GeForce FX5200 128MB AGP card
4.3GB Maxtor IDE HD
Generic IDE CD-RW

It appears that someone on here has had a [similar problem]("http://ubuntuforums.org/showthread.php?t=132951").

Does anyone know anything about this installation issue and, more importantly, know how to get it working? Any advice would be appreciated.

Many thanks!

- Rick

---

### Post by wpshooter on 2006-10-20
Is hard drive completely empty or does it or has it had another O/S on it ?

---

### Post by forfox on 2006-10-20
Cheers for the quick reply!

The first time I attempted to install the server the HD was formatted for FAT32 and had Win 98 installed on it. I tried again after successfully installing from the desktop CD, when there was an ext3 and swap partition.

I have just tried wiping all of the partitions (using fdisk from the Ubuntu live CD) and installing again. Still get the same problem.

---

