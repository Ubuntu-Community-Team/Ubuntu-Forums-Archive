---
title: "installing on a windows SATA system"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by Nevermore on 2007-06-13
Hi everyone
i want to install ubuntu feisty on a system with two sata disks
on /sdb there is a windows installation
on /sda there is a windows partition
i have 100Gb free space on /sda wich i partitioned as following:
15Gb / ext3
83 Gb /home ext3
1Gb /swap

now when i try to install ubuntu from livecd, grub doesn't get installed
i tried to click advanced at the installation window and choose /dev/sda as default grub install
but it didnt work
hd0 that is the default, doesn't work either, i can only get windows to boot but no grub bootloader is installed.

how can i install ubuntu with grub menu on this system?
thanks everyone

---

### Post by logos34 on 2007-06-13
Go into your BIOS and verify that the hard disk boot priority is set to boot first from sda, and that the other drive settings for sda are correct.

You could try to reinstall grub from the live or alternate install cd.  On the latter you'll see a menu option, but for the former you have to type this in a terminal:

[B]sudo grub
find /boot/rootstage1[/B]
(enter the output 'hdx,y' in the next command)
[B]root (hdx,y)
setup (hdx)
quit[/B]

*you could also try putting grub on root partition instead of the mbr.  In place of 'setup (hdx)' above you would type 
**setup (hdx,y)**

verify that linux root partition is flagged 'bootable' ('*'): 
**sudo fdisk -l**

Otherwise download [SuperGrub]("http://supergrub.forjamari.linex.org/").

---

