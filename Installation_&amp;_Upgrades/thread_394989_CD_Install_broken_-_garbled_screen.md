---
title: "CD Install broken - garbled screen"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by downward_spiral on 2007-03-27
Hi,

This is my first foray into Linux, but not computing.  I know that other OS inside out.

Downloaded Ubuntu 6.10 Desktop CD, but I cannot seem to get it working with my setup at all.

I see the boot menu, the splash screen, and then the monitor resyncs and all I get is a screen full of garbage. In some screen modes I get columns of vertical multicoloured bars filling the screen. In others, I can see the desktop, but it is badly garbled. Alternatively I get a blank magenta screen. I can hear the startup sound, though.

I have attempted the fix shown on this thread :
[http://www.ubuntuforums.org/showthread.php?t=287526&highlight=guide+for+those+with+garbled+video](http://www.ubuntuforums.org/showthread.php?t=287526&highlight=guide+for+those+with+garbled+video)

I have edited the config, but upon restarting GDM I always get the message:

GNOME Display Manager   Starting  [fail]

Sometimes CTRL-ALT-F1 brings up a garbled console in the first place and I can't even attempt the fix.

All of this happens in safe mode as well. I have attempted the vga=normal and some other config line entries with no change.

I have verified the CD as being a good copy. I can also run some other distros LiveCDs.

I am using an Nvidia Geforce 6600GT AGP. I have also tried it on a GF 6800 PCI-E system elsewhere with the same results.

Anything left to try? 

David

---

### Post by twistedknight on 2007-03-27
install using your onboard video...
 selecting it in bios and install Nvidia Drivers once system is installed
be sure to switch the cable to the onboard video jack

---

### Post by Dazz on 2007-03-27
I too have this same issue... I've tried every video option under F4 and I get nothing but garbled video.  I don't have onboard video on my machine so I cannot follow twistedknight's suggestion.  Surely someone knows how to fix this...  I've been searching for several hours now with not a single solution working. :(

---

### Post by downward_spiral on 2007-03-28
I resolved this problem myself after spending a night that could've been used to do far better things..

In the startup options, I changed the config line by deleting splash and quiet, and inserting break=bottom in their place.

When the console appeared I entered:

chroot /root nano /etc/X11/xorg.conf

I then changed the Driver "nv" to Driver "vesa" in the device section, saved the file, then exited the editor.

in the console, I typed exit, then:

sudo /etc/init.d/gdm restart

I finally got to the desktop, with graphics which take about a week to open a window. Lovely.

I finally installed it to HD, installed the latest Nvidia drivers (which again took me all night as the install script kept failing and I had to change about a million things), only for the automatic updates to completely break the drivers.

Now the system does not boot, and I have to go back to using Driver "vesa".

What a waste.

---

