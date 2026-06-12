---
title: "/bin/sh: can't access tty: job control turned off"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by mailbox on 2006-10-25
I'm trying to install Ubuntu off a live cd, and it keeps dying with:

/bin/sh: can't access tty: job control turned off

I haven't even installed it yet; I can't get into the live cd. 'Check disc for defects' gives the same error.
If it helps, I'm using an Asus motherboard and an AMD dualcore. I think this might be the problem.
Full specs: Asus A8N32-SLI, AMD x64 X2 4800+, 250gb SATA, 2Ggb DDR400, 7900gtx

---

### Post by mailbox on 2006-10-26
anyone?

---

### Post by _obelix_ on 2006-10-26
Hi,

the same here. I install Edgy on my Laptop: Fujitsu Siemens Lifebook C-6345, Celeron 650, 192 MB RAM.

Regards

obelix

---

### Post by nullmind on 2006-10-26
Same problem after a dist-upgrade from Dapper. I've mounted my Ext2 in XP to view the inittab and posted it below (however, I will likely not have write access from within XP)

**/etc/inittab**
```

# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
#4:23:respawn:/sbin/getty 38400 tty4
#5:23:respawn:/sbin/getty 38400 tty5
#6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3



```

---

### Post by nullmind on 2006-10-26
I haven't fixed my system yet, but it's pointing to the fact that during the upgrade (from within Dapper using the graphical "dummy-proof" interface) it has changed my partition from /dev/hda2 to /dev/hda3 somehow.

I know this because what I used to mount as (0)(1) (hda2) is now (0)(2) (hda3) and when booting I get an error about not being able to mount /dev/hda2.

Hopefully this can be of some help to others.

---

### Post by Rubbing Alcohol on 2006-10-27
I was getting essentially the same thing. I seem to have fixed it on my machine.  In my case, I could get to the grub menu. From there hit 'c' to get to the command line.
```

grub>  root (hd0,1)
           Filesystem type is ext2fs, partition type 0x83
grub>  kernel /vmlinuz root=/dev/hda2
           [Linux-bzImage, setup=0x1c00, size=0x17e851]
grub> initrd /boot/initrd.img-2.6.17-10-386
          [Linux-initrd @ 0x1f966000, 0x67904d bytes]
grub> boot

```

That gets my machine up and running. The drive and partition numbers might be different for others. Once loaded, give yourself root and go fix your /boot/grub/menu.lst file. 

After the update, the root and kernel settings were incorrect in mine which is what was causing the porblem. 

If you can't get to the grub command line, you can try the Super GRUB Disk. This page also helped me quite a bit:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Aurelius on 2006-10-29
I have a similar problem. I can login just fine with the new -386 kernel. Trying to use the -generic kernel, though, results in the "can't access tty" error.

---

### Post by Aurelius on 2006-11-01
Has anyone been able to fix this short of a re-install?

---

