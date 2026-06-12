---
title: "Lilo - no menu given before loading Linux!"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by Mahke on 2005-10-18
Hi guys,

I'm a linux noob dipping his toes in again (I've used Mandrake in the past). I managed (after much work) to get Ubuntu running ok. I found I couldn't run Grub for some reason (it would always give a load error), so installed LILO instead.

Now, it's all running fine (I'm using Ubuntu now, actually), but LILO won't give me an option to boot into Windows when I reboot!

How do I manage this? I have edited my /etc/lilo.conf file to include Windows (I think I did it right) and ran LILO using 'sudo lilo', but no joy.

My .conf file is below - any help will be MUCH appreciated!

(FYI, I run WinXP, on the save drive as Ubuntu - seperate partitions, natch:))

Mark


lilo.conf:

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
boot=/dev/sda

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/sda2

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
delay=20

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

#image=/vmlinuz.old
#	label=LinuxOLD
#	read-only
#	optional
#	restricted
#	alias=2

#	initrd=/initrd.img.old


# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#	label=HURD
#	restricted
#	alias=3
other=/dev/sda1
	label=Windows
#	restricted
#	alias=2

```

---

### Post by Mahke on 2005-10-18
Oh, when I run 'sudo lilo' I get the following:

```
Warning: '/proc/partitions' does not match '/dev' directory structure.
Name change: '/dev/dm-0' -> '/dev/evms/hdc1'
Added Linux*
Added Windows

```

---

### Post by Mahke on 2005-10-19
Anyone? :(

---

### Post by Mahke on 2005-10-19
Easy fix, in the end.

I just added 'prompt' on the line under # install=menu

And that brings up the prompt screen :)

*hand->forehead*

---

