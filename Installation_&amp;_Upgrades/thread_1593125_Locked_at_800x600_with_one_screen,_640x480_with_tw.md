---
title: "Locked at 800x600 with one screen, 640x480 with two screens"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Charbax on 2010-10-11
This has actually been happening since a couple kernel updates ago, I cannot select higher resolution in System > Preferences > Monitors than 800x600 now as I am using one VGA LCD Monitor (which supports  up to 1280x1024) and if I connect my HDTV on the DVI, it blocks both mirrored at 640x480.

This is not limited to 10.10 but has been happening with 10.4 since a few "Automatic updates" ago, the way I would avoid it is to select booting with an old kernel on that choice screen at bootup, I would scroll down to I think kernel [v2.6.32.22 for things to work ok.]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.22-lucid/")

I am using AMD64bit shuttle pc (bought in 2006 or so) with an ATI graphics card (how do I figure out which graphics card model I have?)

---

### Post by Charbax on 2010-10-11
This thread: [http://www.backports.ubuntuforums.org/showthread.php?t=1470952](http://www.backports.ubuntuforums.org/showthread.php?t=1470952)

Talks about ATI and 800x600 and says something about doing:

$sudo nano /boot/grub/menu.lst

and then

kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=b7d1fda9-dc35-4e0e-b0fb-e287929151c6 ro  radeon.modeset=0 quiet splash

and some other guy says something about:

> To clarify for non-hackers, 
 GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0 quiet splash"May these fix my problem? And if so, what do I need to do exactly?

---

### Post by Charbax on 2010-10-11
I connected using DVI only to the HDTV and now the resolution is fine working at 1280x720. Don't know if this may be a VGA only thing or only if I try to connect two screens.

---

