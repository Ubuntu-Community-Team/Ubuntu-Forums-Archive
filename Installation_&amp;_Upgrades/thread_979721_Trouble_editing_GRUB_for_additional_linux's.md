---
title: "Trouble editing GRUB for additional linux's"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by w1av on 2008-11-12
Hi,

I am trying to use an ISO image copied on a small partition to be able to boot from. I have done this before a long time ago and forgot some things. The problem I have is when I boot from the ISO, all goes well till it stops dead saying "Cannot find the filesystem, dropping you to a limited shell".
The problem is the files are too confusing as far as what they do and where the reference to them goes in /boot/grub/menu.lst
I was trying to use the image ISO to a small distro called "Feather Linux" and tried "DSL" and cannot seem to put the right entries in menu.lst.
Different linux distros have different named files! The ones I have problem with are the EXACT name of KERNEL, and 2 files called minirt24.gz and initrd. I keep putting them in the wrong place in menu.lst. Probably cause I dont know what they are or do. Can anyone help? Whjat I do is download the ISO from either DSL or FEATHER LINUX, burn the iso to CD, then copy the whole contents of the CD to a folder in an extra partition. The partition is a FAT32 partition. Should it be an ext3????? And it is hardto find the NAME of the KERNEL or even find the kernel so I cant reference it in menu.lst. Then those other files......Is ther a formula for entries for other os's in menu.lst to make booting them work???? AQgain I am nottrying to boot another INSTALLED linux, just the ISO image cause it boots lightning fast from a HARD DRIVE instead of a CD. So what I am trying to do is boot a LIVE CD IMAGE from hard drive not the actual CD. Am I making sense?????:mad:

---

