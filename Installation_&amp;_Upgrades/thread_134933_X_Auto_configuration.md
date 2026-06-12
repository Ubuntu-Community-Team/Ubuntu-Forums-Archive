---
title: "X Auto configuration"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by haagen on 2006-02-22
Hi,

I'm wondering how the installer does its X windows auto configuration ?

Why ?  Well I am installing workstations using [SystemImager]("http://www.systemimager.org") and I'm trying to support a few differnet types of PCs.  In effect this is making a clone of the system and putting it on different hardware.  Ubuntu seems to handle this fine but the video cards are different so X breaks.

If I install from the Ubuntu CD to any of these PCs it automaticlly detects and configures the hardware perfectly.  I can do ```
dpkg-reconfigure xserver-xorg
``` run through the options and get X working again.

I've tried running ```
Xorg -configure
returns 
Missing output drivers, configuration failed
``` 
So I'm thinking that if the cd installation process can auto configure X then I should be able to re-run that process, with a view to automating it.  The question is how ?  Where in the installer should I look for this process ?

I've been using Linux for quite a few years but I've only recently started working with Debian/Ubuntu type systems (which has been a pleasant expierence).  So I'm hoping some one maybe able to point me in the right direction on how the installer manages X configuration.

---

### Post by haagen on 2006-02-28
To answer my own post maybe it will help someone else.

This script does auto configuration and writes a new xorg.conf make sure you backup your existing xorg.conf before running this.
```

#!/bin/sh
# Based on the script found in http://ftp.linux.org.uk/~dan/livecd
# which is referenced from http://www.linuxjournal.com/article/7246
# Changes made so that the script works with xorg as opposed to xfree
# Mods by Pete Cain

export PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/X11R6/bin
debconf-communicate <<EOF
SET xserver-xorg/autodetect_mouse true
SET xserver-xorg/autodetect_monitor true
SET xserver-xorg/autodetect_video_card true
FSET xserver-xorg/autodetect_mouse seen true
FSET xserver-xorg/autodetect_monitor seen true
FSET xserver-xorg/autodetect_video_card seen true
EOF
sh /var/lib/dpkg/info/xserver-xorg.config configure
dexconf -o /etc/X11/xorg.conf
```

---

