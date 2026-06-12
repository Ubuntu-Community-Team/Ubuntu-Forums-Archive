---
title: "Require Lilo Assistance"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by helpdeskdan on 2006-06-10
Question:
SDA1 - how do I boot from the live/install CD and install lilo (NOT GRUB!!) to the SDA1 partition (not SDA drive)?  

Perhaps unneeded background:
After a very long failed upgrade, I wiped & installed dapper.  However, it installed grub which hosed my system!  After some much needed help from good ol' freedos, I restored my ancient System Commander so I could at least get to windows.  What a bad day!  ](*,)   :cry: I would rather like to rant on the absence of lilo from the installer, but this is not the place.  I was able to do lilo in 5.04!

---

### Post by rcarring on 2006-06-10
I think lilo was removed in Breezy. I don't know for sure, but my vmware supplied install had grub as the bootloader.

Its certainly not about in Dapper.

I guess the devs thought grub was a better boot manager than lilo.

---

### Post by helpdeskdan on 2006-06-10
Well, there's a link to it, but the link is dead. 
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=lilo](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=lilo)

They just released a new version of lilo last Sept.  I could compile it, but I can't boot!  Kind of a chicken and egg problem.  

Maybe I'll have to switch to another distro.  Dang, I liked Ubuntu.

---

### Post by helpdeskdan on 2006-06-10
I can boot and install lilo using aptitude.  However, I have to create a lilo.conf before I run liloconfig and I'm not sure how to do this.  Anybody have an example?

---

### Post by Ahriman on 2006-06-11
[QUOTE=helpdeskdan]I can boot and install lilo using aptitude.  However, I have to create a lilo.conf before I run liloconfig and I'm not sure how to do this.  Anybody have an example?[/QUOTE]
Here is a copy of mine. I had to install LILO because the installer said GRUB doesn't like being installed onto xfs filesystems.
```
# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.

# +---------------------------------------------------------------+
# |                        !! Reminder !!                         |
# |                                                               |
# | Don't forget to run `lilo' after you make changes to this     |
# | conffile, `/boot/bootmess.txt' (if you have created it), or   |
# | install a new kernel.  The computer will most likely fail to  |
# | boot if a kernel-image post-install script or you don't       |
# | remember to run `lilo'.                                       |
# |                                                               |
# +---------------------------------------------------------------+

# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/hda

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/hda1

# This option may be needed for some software RAID installs.
#
# raid-extra-boot=mbr-only

# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller.  Using `compact' is especially recommended when
# booting from a floppy disk.  It is disabled here by default
# because it doesn't always work.
#
# compact

# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu

# Specifies the location of the map file
#
map=/boot/map

# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration.  If a
# command line is given, other than one specified by an `append'
# statement in `lilo.conf', the password will be required, but a
# standard default boot will not require one.
#
# This will, for instance, prevent anyone with access to the
# console from booting with something like `Linux init=/bin/sh',
# and thus becoming `root' without proper authorization.
#
# Note that if you really need this type of security, you will
# likely also want to use `install-mbr' to reconfigure the MBR
# program, as well as set up your BIOS to disallow booting from
# removable disk or CD-ROM, then put a password on getting into the
# BIOS configuration as well.  Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000

# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=100

# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
#	prompt
#	delay=100
#	timeout=100

# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode>)
#
# vga=ask
# vga=9
#


# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
 
# If you used a serial console to install Ubuntu, this option should be
# enabled by default.
# serial=

#
# Boot up Linux by default.
#
#default=Linux

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


# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#	label=HURD
#	restricted
#	alias=3
other=/dev/hdd1
	label=Windows
#	restricted
#	alias=2

```
All I have done to change this from the norm is to comment out the default=Linux line and extend the delay time to 100 deciseconds (why oh why use deciseconds and not regular seconds?).

---

### Post by Herman on 2006-06-11
The 'alternate' Dapper install CD is the one to use if you want to make a custom installation of Dapper Drake. It provides options like installing Lilo or installing  a bootloader to the first sector of the partition or to a floppy disk.
For an install site for the alternate install CD, [*click here*]("http://users.bigpond.net.au/hermanzone/").
Regards, Herman

---

### Post by helpdeskdan on 2006-06-11
Thanks Ahriman and Herman!  I tried to write my own lilo, and even got the lilo package installed, but I couldn't mount dev to install!  :mad: 
Thanks for the link and info the alternative install; this is what I require.  :D

---

### Post by slo on 2006-07-17
I use gentoo before, and it is true that Grub can be install on xfs filesystem, I want to know why on ubuntu it use Lilo when I use XFS

> **Ahriman said:**
> Here is a copy of mine. I had to install LILO because the installer said GRUB doesn't like being installed onto xfs filesystems.

---

