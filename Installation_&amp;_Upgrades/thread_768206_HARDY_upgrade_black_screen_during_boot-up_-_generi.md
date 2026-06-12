---
title: "HARDY upgrade: black screen during boot-up - generic kernel works"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by blazoner on 2008-04-26
I Dist-upgraded from Gutsy to Hardy, and now if I choose **Ubuntu 8.04, kernel 2.6.24-16-rt** in my grub menu, I get a black screen right before the login screen would normally appear. If I choose the **Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode)**, I can get it to boot after having it it chop up my Xorg.conf, but that breaks my nvidia driver.

From my menu.lst file:
```
## ## End Default Options ##

title        Ubuntu 8.04, kernel 2.6.24-16-rt
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-rt root=UUID=366b07b1-1d28-4401-8698-958b23b9e572 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-rt
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-rt (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-rt root=UUID=366b07b1-1d28-4401-8698-958b23b9e572 ro single
initrd        /boot/initrd.img-2.6.24-16-rt

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=366b07b1-1d28-4401-8698-958b23b9e572 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=366b07b1-1d28-4401-8698-958b23b9e572 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, kernel 2.6.22-14-rt
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-rt root=UUID=366b07b1-1d28-4401-8698-958b23b9e572 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-rt
quiet

title        Ubuntu 8.04, kernel 2.6.22-14-rt (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-rt root=UUID=366b07b1-1d28-4401-8698-958b23b9e572 ro single
initrd        /boot/initrd.img-2.6.22-14-rt

title        Ubuntu 8.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
``` By choosing **Ubuntu 8.04, kernel 2.6.24-16-generic** I have been able to get an x-session going, and reinstall my nvidia drivers.
Even so, I still haven't been able to boot up **Ubuntu 8.04, kernel 2.6.24-16-rt**.
I'm out of my depth here. What's my next step?

---

### Post by blazoner on 2008-04-26
Anybody....?

---

### Post by mikenna@cox.nety on 2008-04-27
I am a new Linux user.  Using an Acer 5102LMi laptop.  Loaded and ran Gutsy flawless.  Upgraded to Hardy 8.04 got to the question do you want to restart your computer clicked yes and nothing but a black screen.  Tried to load disc 32 or 64 both and still get black screen.  Any help out there for my problem way lost.  It says I have a Bios Bug?

---

### Post by chronographer on 2008-04-27
I would try a new xorg.conf file. you need to back up your old one first, if you can get to a terminal (from the black screen you should be able to press crtl alt F1 through F7 to get to a terminal, F7 should be your X session) then type 

"sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.OLD"

and then you can try one of 2 things, 

1/ an automatic xorg.conf generation by "sudo dpkg-reconfigure xserver.xorg"
2/ delete the xorg.conf and try running with Ubuntu making it up as it goes along! "sudo rm /etc/X11/xorg.conf" *MAKE SURE YOU BACK UP YOUR OLD ONE FIRST!!!!!!*

You should be able to get xorg working using the default nv drivers if nvidia doesn't work. Good luck!

---

