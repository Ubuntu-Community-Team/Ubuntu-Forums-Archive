---
title: "[SOLVED] Install problem: Cannot launch Live CD/get past GRUB"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by tghe-retford on 2008-03-27
I built my own PC today and I am trying to install and get Kubuntu 64-bit, which my new processor supports running. However, I am hitting a lot of problems doing so.

I have the alternative CD and when I select the options to start Kubuntu or use safe graphics mode, I get as far as "Loading... Please Wait" and the display will cut out, as if it is getting no signal. Trying the VGA option for a resolution my monitor supports (ie. 1280x1024x32) has no effect. Only a hard reset gets the computer working again. When I tried the "no splash" suggestion, I get as far as "loading boot script from etc/local.rc" (or something like that) and the computer will stop, regardless of how long you leave it. I can reset using CTRL+ALT+DEL.

I managed to install Kubuntu on my hard disk using the text based install, but that only gets past GRUB and as far as the "Loading... Please Wait" prompt before the screen cuts out again. If I edit GRUB to include "no splash" the same "loading boot script from etc/local.rc" scenario occurs.

I can only do anything from the recovery option which disables the ethernet connection I use for the Internet so I have no net access on the new PC.

My current setup:

ASUS P5N-E SLI Motherboard
Zotac 8800GT 512MB PCI-Express Graphics Card
Intel Core 2 Quad Q6600 2.4GHz
2GB OCZ RAM at 800MHz
Maxtor 500GB Serial ATA Hard Disk
Sony DVD+/-RW disc drive

I am completely out of ideas and at the moment, I am writing this post from the PC I sold to my mate which helped pay for the new PC. I have them setup side by side so if anyone has any ideas, I can try anything out immediately.

I don't want a £600+ expensive doorstop nor do I want to install Windows on it either. :( Any suggestion would be most welcome and appreciated.

Thanks in advance.

---

### Post by phidia on 2008-03-27
I think you might try the livecd both 32 bit &64 bit versions-although I'm sure you want to use the 64 bit version on your newly built computer.

Sometimes selecting the versa driver will get a useable gui, and that's why I'm suggesting the livecd because you can play around to see what will get a working desktop.

It seems theat you have a nvidia card-you should be able to get the nvidia driver working on that card check the video and multimedia [forum]("http://ubuntuforums.org/forumdisplay.php?f=138") for more specifics if you need them. Hope that helps.

---

### Post by tghe-retford on 2008-03-27
> **phidia said:**
> I think you might try the livecd both 32 bit &64 bit versions-although I'm sure you want to use the 64 bit version on your newly built computer.
I have a 7.04 64-bit live CD which I have tried and I finally have a GUI and with a second ethernet cable, a network connection to the Internet. I can also see my hard disk partitions. Where should I go from here?

Thank you for your help so far.

---

### Post by tghe-retford on 2008-03-27
I finally managed to get to the KDE desktop on my PC, by doing the following:

[LIST]
[*]I edited my /etc/X11/xorg.conf file and changed the driver from "nv" to "vesa"
[*]I then edited the GRUB entry for my normal boot by pressing "e", then selecting the line with kernel, pressing "e", changing "splash" to "nosplash", pressing enter and then pressing b to boot. The KDE desktop appeared soon afterwards.
[/LIST]

Now just to get the 8800GT driver installed. :)

---

### Post by phidia on 2008-03-27
[This]("http://ubuntuforums.org/showthread.php?t=301499") might help with the driver.

---

