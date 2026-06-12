---
title: "Installation from USB-Drive"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by thrasher on 2005-11-23
Hi! 

I got a hint from a guy at college that i should give ubuntu a try, since my suse 10 doesn't seem to like our college's wlan and it looks like yast is meddling with my configuration. 

I just downloaded the cd-image and tried to install on my notebook, but after booting from cd it can't locate the drive for installation sources since it's an extern usb-drive. 

Loading modules by floppy isn't an option, since my notebook doesn't have a drive. 

Any options for installation? could i use the cd just for booting and then mount a fat32-partition for installation files? 
is there any possibility to even use this drive after installation? 

(btw it's a cheap drive from mashita - never heard of it before, but it came with my notebook)

---

### Post by kalin on 2005-11-23
I'm not sure exactly what you mean by installing "from" USB-Drive, do you mean installing *to* an external USB drive? If that's the case here's a guide on how to do it:
[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

---

### Post by thrasher on 2005-11-23
no, i meant that the only cd drive on my notebook is an external which is connected by usb... 

short summary: when i insert the installation cd it boots but when setup tries to mount the installation source it fails choosing a module for my drive...
And i don't see the possibility to load modules from floppy since i got no drive :???:

---

### Post by yesplease on 2005-11-23
Perhaps this helps

HOWTO: Install Ubuntu Linux without burning a cd - 04-22-2005

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

or the guide it refers to.

I hope somebody has a simpler solution for you.

---

### Post by thrasher on 2005-11-23
hey, thanks! 

that's not a bad idea, since i already have grub configured to boot suse it's not a big deal to boot installation from another partition...if installation does pick up the files from there it should be no problem...

i'd give it a try, thanks again

thrasher

---

