---
title: "Live works, install doesn't"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by EBFoxbat on 2006-06-13
I'm trying to put Ubuntu on my Dell XPS 400 w/ 256 MB PCIe GeForce 6800.

I tried for a long time a while ago, and gave up in frustration. After a break to compose myself, I'm going to try again.

I can get Live to work fine on the computer, except for network support. I install it fine, but I get no network support and cannot for the life of me get my graphics working right, I think it's X that wont configure.

Is there a way to see how Live configures stuff and just copy that?

I can't apt-get video drivers because I have no network. I don't know enough command line stuff to burn the appropriate files on to a CD and run that. 

I believe there is a specific fix for the E1000 type network devices.

I really really need someone to walk me through this. I'm dieing to have Ubuntu working on this computer.

---

### Post by xfile087 on 2006-06-13
[QUOTE=EBFoxbat]I'm trying to put Ubuntu on my Dell XPS 400 w/ 256 MB PCIe GeForce 6800.

I tried for a long time a while ago, and gave up in frustration. After a break to compose myself, I'm going to try again.

I can get Live to work fine on the computer, except for network support. I install it fine, but I get no network support and cannot for the life of me get my graphics working right, I think it's X that wont configure.

Is there a way to see how Live configures stuff and just copy that?

I can't apt-get video drivers because I have no network. I don't know enough command line stuff to burn the appropriate files on to a CD and run that. 

I believe there is a specific fix for the E1000 type network devices.

I really really need someone to walk me through this. I'm dieing to have Ubuntu working on this computer.[/QUOTE]

I'm not 100% sure, but once booted into the live CD you may find the xorg configuration in /etc/X11/xorg.conf. If that is so you may be able to copy it to another drive and use once you've installed dapper.

from the terminal: **sudo cp /etc/X11/xorg.conf /path to other drive/xorg.conf** and to copy back just reverse **sudo cp /path to other drive/xorg.conf /etc/X11/xorg.conf**

---

