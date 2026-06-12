---
title: "No Video -- Ubuntu 7.10 / GeForce 7900GS"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by Lagged2Death on 2007-11-28
I just put together a new PC. I installed Windows Vista but left unpartitioned space on the hard disk with the intent of installing Linux as well. I've got the Windows stuff working well, so I'm confident the hardware is working.

I downloaded "ubuntu-7.10-desktop-i386.iso" and burned it to CD. I set up my BIOS to boot from the CD drive. I booted the Ubuntu CD, and the menu appeared OK. I used the "check CD for defects" option, which confirmed the CD was OK.

Then I tried booting Ubuntu. Choosing either "Start or install Ubuntu" or "Start Ubuntu in safe graphics mode" produced the same result:

[IMG]http://img136.imageshack.us/img136/5552/boot3fa9.jpg[/IMG]

This was followed by a brief glimpse of a blank desktop and a working mouse pointer, followed by a blank black screen. When I tried "Start or install Ubuntu," the monitor actually went into no-signal/standby mode at this point. When I tried "Start Ubuntu in safe graphics mode," the monitor remained active, but still showed a blank black screen.

This system has a Gigabyte GA-P35-DS3L v2 motherboard and a PNY GeForce 7900 GS PCIe video card. The monitor is connected via DVI. There is no motherboard-integrated video, and I don't have any other PCIe graphics cards.

I've played with Live CD Linux distros on other PCs before. I was really looking forward to installing Linux for real. Any tips much appreciated!

**[Edit]** Here's something else I've discovered. I looked around and found an old Ubuntu 6.06 CD in a pile of older stuff. I can boot from that just fine. It even figures out my monitor's top resolution correctly. I'm posting this edit from it now. It was my understanding that newer versions were friendlier in terms of helping novices set up dual-boot systems, which is why I tried the latest thing. Maybe that's not the way to go after all? Any tips still much appreciated.

---

### Post by ceargle on 2007-11-28
Same thing happened to me a few times when booting the 7.10 AMD64 LiveCD. 

Once you the screen goes black, try hitting Ctrl+Alt+Backspace to restart X. This fixed the problem for me, hope it helps.

---

### Post by dabl on 2007-11-28
My EVGA GF 7900GS has worked great in all versions of *buntu since Dapper, both 32-bit and 64-bit.  But my Samsung monitor only has the conventional 15-pin video connector, so I've never played with the DVI output.

When you get the black screen, did you ever try Alt-F1 or Ctrl-Alt-F1?  If you get a text login screen, then it's just a driver problem.  You can configure it as a VESA driver, then when that is up and running you can install the Nvidia driver from there.

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:)

---

### Post by Lagged2Death on 2007-11-29
It seems that, confronted with a blank screen, I had not tried anything as simple as pressing any keys. Pressing just about any key (like Ctrl or Alt) brings the desktop back immediately, almost as if the desktop manager had activated a screensaver. (Although booting from the CD is slow, it's not *that* slow.) Oddly, though, the desktop resolution may be different on different boots.

I will look into the instructions in your link in particular, dabl. Thank you both for your answers!

---

