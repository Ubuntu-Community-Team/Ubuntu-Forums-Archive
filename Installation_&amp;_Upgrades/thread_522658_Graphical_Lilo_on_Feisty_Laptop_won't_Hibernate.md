---
title: "Graphical Lilo on Feisty Laptop won't Hibernate"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by JeffB on 2007-08-10
I am a new Ubuntu user -with i386 (32-bit) Ubuntu Feisty 7.04 dual-boot installed alongside XP; on a brand new Dell Inspiron 1501 laptop; with an AMD 64-bit Athlon X2 processor; and a Radon Video Card.

After installing Ubuntu into its own partition, I use the primary bootloader XOSL; installed on it's own separate, dedicated partition, as my main bootloader;  and pass from there to either XP or Ubuntu.

I like, and use freeware, "XOSL" its graphical, clean and easy to fix when problems happen and works with both windows and linux in making this transition to Linux.

But my fiancee  also uses this computer, and when it gets to Ubuntu it confuses her and others I am showing linux to: people that are just used to Microsoft Windows making things much more attractive and easier for them to grasp --without a lot of texty jargon and flickering startups, and blinking monitor mode changes --then the text-based confusing mess that Grub currently is  as soon as it gets passed its  own startup on the Ubuntu Feisty partition.  

For all the good of Ubuntu, (and I do love it for many things ) the first thing my friends  see from Ubuntu, however, is all that black and white Grub mess.

And, by the way, also a really texty, blinky, screen-filling mess --when they try to hibernate on Feisty on a laptop out of the box.

So after trying out various versions of Lilo or Grub; Graphical-Grub; and  Graphical-Animated-Lilo, on many other computers, I am most familiar with just basic Lilo; and having learned it, and especially with it's bitmap menu, and bmp-retain options, I find it does what I need.

It gives me a simpler  than  Grub and more graphical boot.

Lilo just gets me quickly and cleanly to linux .  And I wish Lilo had just been an Ubuntu install option.

I like a lot about Ubuntu --but like I say the black-and-white default grub boot-up on Ubuntu is just jarring; as well as being unnecessary for me; since,  as I say, I am already happy with XOSL's and Lilo's smoother features. 

But now I have a problem: 

Ubuntu is just  still not "nice" for lilo --since I droped grub, and installed it instead. 

When I bootup now, I do get to the graphical lilo boot --and it passes to the Ubuntu usplash and working orange progress bar perfectly before passing to the linux logon; as it should --only  now, at shutdown time,  for me,  Ubuntu just shows a black screen.

--with no orange shutdown progress bar --or graphics --at all. 

The laptop seems to blink into its framebuffer mode --but from there it just stays all black   --and then shuts down after a few seconds.

 And, additionally, worse,  the laptop in Ubuntu will now not hibernate at all. 

Instead of Ubuntu hibernating, the screen --like now at the defective shutdown  --just goes black, and the computer shuts down.  And when I restart, it simply goes to a fresh restart, and and the Ubuntu doesn't recover as hibernated.

All this worked --abiet,  as I say, with a big texty mess --on Ubuntu, with XOSL as a primary bootloader passing to Grub, before I switched to Lilo.

To install Lilo, I rewrote the fstab file --as others on the Ubuntu forum have also done --and also ran sudo dpkg-reconfigure usplash, and also sudo update-initramfs. 
 
Below is my own lilo config file, and my fstab file.

I think maybe the problem is related to the fact that I've manually set lilo to vga=791  --so that lilo can display the graphical bitmap.  

But is Ubuntu's own startup and shutdown graphics needing a different setting? 

Is this lilo video setting also the reason the computer can't seem to save the laptop's state --now at hibernation? 

Or, is it the new fstab, compatible with lilo --that is, nevertheless, just incompatible with Ubuntu shutdown graphics, and hibernation?

Anybody got any ideas on how I can just keep lilo on Ubuntu--and just get the laptop to show the graphics and progress bar at shutdown again?

As well as to get it to hibernate again properly? 
 
I do not want to return to Grub.

Thanks

JeffB


---------------------------------------------------------------------------------
/ETC/FSTAB

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda9       /home           ext3    defaults        0       2
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
# UNCONFIGURED FSTAB FOR BASE SYSTEM


---------------------------------------------------------------------------
--------------------------------------------------------------------------

/ETC/LILO.CONF

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
boot=/dev/sda7

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/sda7

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
install=bmp

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
delay=10

# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
	prompt
#	delay=100
	timeout=100

# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode>)
#
# vga=ask
# vga=9
#

###ADDED BY JEFF FOR GRAPHICAL BOOT
vga=791

bitmap=/installed/ubuntuyellow.bmp
bmp-colors=8,,,10,,
bmp-table=90p,145p,1,15,17
bmp-timer=50p,245p,12


verbose=-5
bmp-retain

####END ADDED BY JEFF FOR GRAPHICAL LILO BOOT




# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
append="quiet splash"
 
# If you used a serial console to install Debian, this option should be
# enabled by default.
# serial=

#
# Boot up Linux by default.
#
default=Ubuntu

image=/vmlinuz
	label=Ubuntu
	root=/dev/sda7
	vga=791
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
#other=/dev/sda2
#	label=Windows
#	restricted
#	alias=2

---

