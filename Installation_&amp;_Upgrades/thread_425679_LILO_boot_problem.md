---
title: "LILO boot problem"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by dahamsta on 2007-04-27
I installed from the alternate CD, which chose LILO instead of Grub for some reason. I'm not getting a graphical boot screen and it's not pausing for me to choose an OS in any way, it just goes from BIOS messages to LILO to booting Linux. How can I get to Windows, and how can I switch to grub? I installed grub via Synaptic and I was all ready to configure it, but the pkg didn't even create /boot/grub, never mind the config files!

adam

---

### Post by confused57 on 2007-04-27
I've never used Lilo, but maybe something here will help:
[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)

---

### Post by psusi on 2007-04-27
Are you using software raid?

Edit your /etc/lillo.conf to change the timeout and such and reinstall by running lilo again.

---

### Post by dahamsta on 2007-04-27
I got a boot screen by hitting CTRL when I was going for the three finger salute; is LILO really that bad that they can't do a graphical boot screen?

Anyway, I can get to Windows now but I have the old faithful hal.dll error, happens every time on this bloody rig.

I'd sitlll be interested in info on how to switch from LILO to Grub, LILO's too much of a PoS to keep. There must be a script out there for it.

adam

---

### Post by Herman on 2007-04-28
Hello dahamsta,

Try this, [                                                                         Re-install GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")..........(with Alternate CD Rescue mode)
When you get to the step fig11 type (hd0) on the line to install Grub's IPL to MBR in your first hard disk.

That should work but if it doesn't just let me know and I'll explain another way, there are lots of ways to install Grub.

Also, you don't need to delete Lilo when you install Grub either, we can use them both, I often have LiLo installed with it's IPL in the Ubuntu boot sector, and Grub's IPL in the MBR. That has proven to be a good way to set things up.

Regards, Herman   :)

---

### Post by psusi on 2007-04-30
Yes, lilo can do a graphical screen, but has to be configured to do so.  The installer installs grub by default, which is why I asked if you are using a software raid, because if you are, grub will not work, so the installer uses lilo instead.

---

### Post by dahamsta on 2007-04-30
I ended up reinstalling, the install borked my boot.ini in Windows too. I fixed that, but then I couldn't see a shared FAT32 partition because LILO set it to hidden at every boot.

I hate LILO, can't understand why the useless piece of crap still exists. Back to good old Grub in the new install, and lo and behold, everything works perfectly! :)

Thanks,
adam

---

### Post by SBFC on 2007-05-17
> Yes, lilo can do a graphical screen, but has to be configured to do so.

Could you please explain this one? I popped in one of my old IDE's that has XP on it before reinstalling Xubuntu. Looking at /etc/lilo.conf it clearly detected the windows drive and has it set up as a menu entry, but I can't figure out where to tell it to actually prompt me for an OS to load.

Thanks.

EDIT:

> # Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu


Not sure how I missed that during the first few passes....

EDIT2:

Ok...I uncommented 'install=menu' and ran the 'lilo' command and after rebooting I'm still not prompted with a menu. Any ideas?

```
oblivion@nippon:~$ sudo lilo
Password:
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/.static/dev/mapper/vg1-root'
    The kernel was compiled without DEVFS, but the '/dev' directory structure
        implements the DEVFS filesystem.
Added Linux *
Added LinuxOLD
Added Windows
The Master boot record of  /dev/sda  has been updated.
Warning: /dev/sdb is not on the first disk
The Master boot record of  /dev/sdb  has been updated.

```

Does that warning have anything to do with it?

And just in case it helps with anything, here's my lilo.conf file.

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
boot=/dev/md0

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/mapper/vg1-root

# This option may be needed for some software RAID installs.
#
raid-extra-boot=mbr-only

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
install=menu

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


# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#	label=HURD
#	restricted
#	alias=3
other=/dev/hda1
	label=Windows
#	restricted
#	alias=2

```

---

### Post by Wim Sturkenboom on 2007-05-17
> **dahamsta said:**
> I hate LILO, can't understand why the useless piece of crap still exists. Back to good old Grub in the new install, and lo and behold, everything works perfectly! :)Lilo has one major advantage over GRUB; it fits fully in the MBR. GRUB always needs to store part of itself outside the MBR (on a partition); if this partition gets corrupted or removed, you will not be able to boot (into any installed OS). You will not have this problem with Lilo.

For that reason, I prefer Lilo a 1000 times over GRUB.

---

### Post by Herman on 2007-05-17
Hello SBFC,
Have you [Run Liloconfig]("http://users.bigpond.net.au/hermanzone/p4.html#Run_Liloconfig")? :)

Regards, Herman :)

---

