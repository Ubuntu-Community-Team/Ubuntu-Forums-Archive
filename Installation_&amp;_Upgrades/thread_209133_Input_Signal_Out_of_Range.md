---
title: "Input Signal Out of Range"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by darkreality on 2006-07-04
First off, sorry if this has been answered, I wasn't able to find it anywhere.

That being said: my problem is a short one: I have an LCD Monitor (Flatron L1715S) on my computer. Upon attempting to install Ubuntu (or even start it from the image) the kernel loads, etc. but suddenly (apparently once it starts loading the actual desktop and XServer I guess), I get the "Input signal out of range" message from my monitor.

Having had this problem with SuSE before, I simply attempted to boot at a lower resolution, which fixed the problem with SuSE. But not with Ubuntu. Not even "640x400 at 16 bit color" fixed the problem. Nor did any other menu option. 

What I'm looking for is pretty much a boot option to make this work. Is there any way to make it work? Because I can't really configure anything to make it work without getting it to boot and letting me see what's going on XD

Thanks in advance.

---

### Post by yabbadabbadont on 2006-07-04
I don't know how the installer will like it, but you could add "vga=normal" as a boot option so that it will boot in text mode.  It may still mess up when it tries to start x-windows though.

---

### Post by feenberg@nber.org on 2006-07-09
I had the same problem, and was able to complete the install only by substituting a CRT for the LCD monitor. There are lots of options offered that look like they would provide a means to cure this, but none of them seemed to:

1) Safe graphics mode -- same problem
2) text mode -- same problem
3) F5-VGA allows one to change the resolution but not the 
   frequency -- same problem

I tried other LCD monitors, also but none around here could accept the frequency used in the Ubuntu 6.06 install. My guess is that I'm missing something - won't most users have LCD monitors nowadays? It hardly seems likely that the default installer wouldn't be compatible, especially since the cure (reducing the frequency) is so trivial.

Dan Feenberg

---

### Post by shuflie on 2006-07-09
I got the same with the AMD64 install DVD. Downloaded the i386 install and it got a bit further, instead of a blank screen I was greeted by an error saying there was a problem with the xserver setup. I edited /etc/X11/xorg.conf (used sudoedit etc/X11/xorg.conf)to remove the higher screen resolutions my graphics card (a Radeon X800 pro) doesn't support in VESA mode (deleted everything higher than 1280x1024 in the 24 bit section). Saved the xorg.conf  file and typed startx to get xserver running. I'm now typing this in the liveCD environment, won't be installing tonight though, this has taken far too long already.

---

### Post by alientrader on 2006-12-16
same problem here, I never make it to prompt screen. may reinstall Breezy unless someone has a better idea. Btw, if installed ati drivers will not be overwritten during upgrade? I have a radeon 9600 pro.

---

### Post by Brian Smith on 2006-12-17
> **darkreality said:**
> First off, sorry if this has been answered, I wasn't able to find it anywhere.

That being said: my problem is a short one: I have an LCD Monitor (Flatron L1715S) on my computer. Upon attempting to install Ubuntu (or even start it from the image) the kernel loads, etc. but suddenly (apparently once it starts loading the actual desktop and XServer I guess), I get the "Input signal out of range" message from my monitor.

Having had this problem with SuSE before, I simply attempted to boot at a lower resolution, which fixed the problem with SuSE. But not with Ubuntu. Not even "640x400 at 16 bit color" fixed the problem. Nor did any other menu option. 

What I'm looking for is pretty much a boot option to make this work. Is there any way to make it work? Because I can't really configure anything to make it work without getting it to boot and letting me see what's going on XD

Thanks in advance.


Maybe a good idea would be to copy the known working Xorg.conf section from the SuSE-created file and paste them appropriately into a server installation from the alternate install CD, then installing the desktop of your choice from the command line.  I similarly struggled on one installation, unable to feed a boot parameter to a normal installation CD to achieve a working Xorg.conf, both in Dapper and Edgy, but I manually edited the Xorg.conf using parameters suggested by a user on this forum, and I thien had a working GUI.  

Stick with it, and good luck.  It's worth it once you get there!

---

