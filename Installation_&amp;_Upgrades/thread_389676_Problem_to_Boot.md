---
title: "Problem to Boot"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by ibuntutoo on 2007-03-21
I have been trying to install Ubuntu onto a 233mhz IBM thinkpad with 192mb of ram. I have tried Xubuntu, Kubuntu, as well as the alternative boots. I get to the boot screen with all but any option I select gets the same results the screen begins to load the kernel and it seems to load and then the screen turns off and it reboots. I have tried install with most of the modifiers unsuccessfully. I was able however to install Puppy Linux, but I am sorry to say that is one ugly puppy. Please I want ubuntu, read my signature.

---

### Post by musther on 2007-03-21
The easiest way (I've found) to get Ubuntu onto a machine which completely refuses to run the installer is to whip out the hard drive, put it in another machine, install, and swap it back.  This being a laptop makes it harder, but still possible.  

However, given the speed of your laptop, Ubuntu will be uncomfortable, although it should work (if you can get it to install).  If I were you I'd use puppy on that machine, you said it's ugly, well there are themes for it, and for its size and speed it really is very very good, and capable.

If you're sure you want to use Ubuntu on it, the above is my best suggestion, use one of those external USB drive housings if you have or can borrow one.  Then plug it into a machine which can boot from USB and install Ubuntu on it.  After this put it back in the laptop, boot Puppy from a CD, use it to edit the file /etc/fstab to suit the new situation, and copy puppy's xorg.conf to /etc/X11/xorg,conf on the hard drive, reboot and you should have Ubuntu.

The wiki contains a lot of info:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Specifically in the advanced section, many creative ways to get Ubuntu onto a system which wont run the installer.

---

