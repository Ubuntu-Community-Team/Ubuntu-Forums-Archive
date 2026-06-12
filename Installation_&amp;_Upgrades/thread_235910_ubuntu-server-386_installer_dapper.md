---
title: "ubuntu-server-386 installer dapper"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by ddave01 on 2006-08-13
I wanted to report an experience that I was able to reproduce several times on a EPIA-M SBC with 400GB hard disk.

The first three installation ubuntu-server proceeded with out any issues however, it ended in an infinite reboot loop.

I installed xubuntu desktop.  The install when satisfactorily and it rebooted into the desktop without any problems.

The BIOS on the EPIA-M was set to automatic for access to the new Samsung 400GB PATA harddisk.

I changed the BIOS settings to LBA in the hope that ubuntu-server would see the harddisk geometry in LBA terms and install correctly.  Install failed with grub Error 18. 

It would appear that the ubuntu-server installer is seeing the drive geometry as being around 560GB when viewed with fdisk via floppy installed tools.

The basic installer ubuntu-server has clearly a different way of recognising and partitioning large disks compared with ubuntu desktop and debian releases.

I am trying the ubuntu-server install on an other system to get more experience.

Does ubuntu-server have the same "installer engine" as the desktop releases?  The desktop installer has not failed us.

---

