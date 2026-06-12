---
title: "Lilo hides partitions"
date: 2005-05-13
forum: Installation &amp; Upgrades
---

### Post by radl33t on 2005-05-13
/dev/hda1 = WinXP
/dev/hda2 = FAT32 (Shared Storage)
/dev/hda3-6 = Unbuntu 5.04

I use a menu option to boot to either windows or ubuntu. When I boot to WindowsXP, Lilo hides hda2. Running Partition Magic under Windows simply shows a hidden fat32 partition. It can, of course, try to fix this, but Lilo will re-hide the partition on reboot.

What is the story? I've dealt with this for nearly 3 months now, but I will be forced to either go back to Fedora or quit Linux entirely if it isn't soon resolved! :( Halpe!

# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.

boot=/dev/hda

root=/dev/hda3

compact

#install=menu
bitmap=/boot/debianlilo.bmp
bmp-colors=1,,0;9,,0
bmp-table=106p,144p,2,9,144p
bmp-timer=514p,144p,6,8,0
install=bmp

map=/boot/map

	prompt
#	delay=100
	timeout=100

vga=normal

default=Linux

image=/vmlinuz
	label=Linux
	read-only
#	restricted
#	alias=1

	initrd=/initrd.img

image=/vmlinuz.old
	label=LinuxOLD
	read-only
	optional
#	restricted
#	alias=2

	initrd=/initrd.img.old

#other=/dev/hda2
#	label=fatshare
#	restricted
#	alias=3

other=/dev/hda1
	label=Windows
	table = /dev/hda
#	restricted
#	alias=2

---

### Post by Mattte on 2005-06-18
I have the exact same problem as you, even the exact same drive partitioning :)

Have you solved it?

---

### Post by Mattte on 2005-06-18
Problem solved. Three lines need to be added to lilo.conf, they tell lilo not to hide the partition when booting windows:

other=/dev/hda1
        label=Windows
        ### ADD THIS, but with your values of course ###
        change
          partition=/dev/hda2
          set=ntfs_normal


The ALTERNATE part of lilo.conf manual tells a little about this.

/Mattias

---

