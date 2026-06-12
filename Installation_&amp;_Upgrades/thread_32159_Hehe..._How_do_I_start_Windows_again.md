---
title: "Hehe... How do I start Windows again?"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by Kizo on 2005-05-06
So...
I've never tried Linux before, and this is what I did.

I got one 80Gb HDD on my Laptop, so I made another partition that I could install Ubuntu on.
Meaning, I still kept Windows on my C:\ (Windows language. :))

During the installation, it couldn't install GRUB, don't ask me why.
So I installed LILO instead.
And here is my question, how do I do if I want to start the computer with Windows again?
What I want the most is for the computer to ask what OS to boot with.

Am I suppose to edit the lilo config in /etc/?
But there are dangerous warning texts there, so I do not dare to change anything without some help.

How does this work?

(Yes, I'm a newbie, when it comes to Linux.)

---

### Post by dave9191 on 2005-05-06
This is an example lilo file i just borrowed from the gentoo handbook
```

boot=/dev/hda             # Install LILO in the MBR
prompt                    # Give the user the chance to select another section
timeout=50                # Wait 5 (five) seconds before booting the default section
default=gentoo            # When the timeout has passed, boot the "gentoo" section

# For genkernel users
image=/boot/kernel-2.6.11-gentoo-r3
  label=gentoo
  read-only
  root=/dev/ram0
  append="init=/linuxrc ramdisk=8192 real_root=/dev/hda3 udev"
  initrd=/boot/initrd-2.6.11-gentoo-r3

# The next two lines are only if you dualboot with a Windows system.
# In this case, Windows is hosted on /dev/hda6.
other=/dev/hda6
  label=windows


```

Im assuming that your lilo file looks similar and you dont want to edit that. But you want to add the last couple of lines in. Of course it has to point to your partion where windows is. If you had windows installed first then its most likely going to be /dev/hda1 (first hard drive - a, first partion). And the label can be anything you want it to be called (like WindowsXP). 

This should pop up a menu for you to choose what OS to boot. 

Dave

---

### Post by kvidell on 2005-05-06
[QUOTE=dave9191]Im assuming that your lilo file looks similar and you dont want to edit that. But you want to add the last couple of lines in. Of course it has to point to your partion where windows is. If you had windows installed first then its most likely going to be /dev/hda1 (first hard drive - a, first partion). And the label can be anything you want it to be called (like WindowsXP). 

This should pop up a menu for you to choose what OS to boot. 

Dave[/QUOTE]
 Don't forget to restart LiLO before you reboot after you make changes to the config file.

---

### Post by Kizo on 2005-05-06
This is my lilo.conf

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
root=/dev/hda5

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
vga=normal

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
	label=Windows3
#	restricted
#	alias=2

```

So, please tell me what to change to what, and then, how do I run LILO?
I really don't wanna mess things up so bad I can't boot any of the systems. 

And I had Windows installed prior to the Linux installation.
In "Windows Language" I had Windows XP Home, on C:\ while making another partition called F:\ (DVD, etc, in between.)

I REALLY appriciate the help.
Thanks.

---

### Post by dave9191 on 2005-05-06
Well you already have windows in the options. And you dont get a meny showing when you start your computer? It should show for about 2 sec with those settings. 

And to put your mind to ease, if you badly screw up with bootloader settings, then it is possible to restore the windows settings using the windows cd. Just put the windows cd in, boot from it, go to the console and type

fixmbr

say that you want to overwrite the master boot record and next time you boot you will load into windows. then you will have access to the net and the forums to ask for more help if you need it. You can also boot from Linux live cds to fix lilo or grub. 

But back to your prob, you dont get a menu at all?

and to tun lilo after you edit the config file, try 

sudo /bin/lilo

im guessing thats where lilo would be stored. If not do a 

sudo updatedb
locate lilo 

and run the command using its full path.

---

### Post by Kizo on 2005-05-06
[QUOTE=dave9191]Well you already have windows in the options. And you dont get a meny showing when you start your computer? It should show for about 2 sec with those settings. 

And to put your mind to ease, if you badly screw up with bootloader settings, then it is possible to restore the windows settings using the windows cd. Just put the windows cd in, boot from it, go to the console and type

fixmbr

say that you want to overwrite the master boot record and next time you boot you will load into windows. then you will have access to the net and the forums to ask for more help if you need it. You can also boot from Linux live cds to fix lilo or grub. 

But back to your prob, you dont get a menu at all?

and to tun lilo after you edit the config file, try 

sudo /bin/lilo

im guessing thats where lilo would be stored. If not do a 

sudo updatedb
locate lilo 

and run the command using its full path.[/QUOTE]
Nope, I don't get a menu at all.
When I start it I first get the Fujitsu Siemens screen, and then:
LILO 22.6.1 loading linux.......

---

### Post by dave9191 on 2005-05-07
Ok, in that case try this 

#
# Boot up Linux by default.
#
default=Linux

comment out the default part so you have 

#
# Boot up Linux by default.
#
#default=Linux

and run lilo. 

If that doesnt work, then try hitting tab when it says loading linux or holding alt or shift before lilo loads. 

If that doesnt work I cant help you. I prefer grub and ive only used lilo once when grub failed to work as I had the boot partion too far on the hard disk .

Dave

---

### Post by Kizo on 2005-05-07
[QUOTE=dave9191]Ok, in that case try this 

#
# Boot up Linux by default.
#
default=Linux

comment out the default part so you have 

#
# Boot up Linux by default.
#
#default=Linux

and run lilo. 

If that doesnt work, then try hitting tab when it says loading linux or holding alt or shift before lilo loads. 

If that doesnt work I cant help you. I prefer grub and ive only used lilo once when grub failed to work as I had the boot partion too far on the hard disk .

Dave[/QUOTE]
Wow, you sure are the all might when it comes to this.
All I had to do was press Shift while the "Loading LILO" thingy was there. :)
Wahey!

And about Grub, I couln't install it. Don't ask me why, but it said it couldn't install, and I tried several times, that's why I use LILO.
Thanks alot!

---

### Post by dave9191 on 2005-05-07
Glad I could help :) 

Enjoy, 

Dave

---

