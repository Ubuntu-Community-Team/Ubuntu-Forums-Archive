---
title: "Low graphics mode noapic install finally works, now no USB."
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by trixx on 2010-04-04
Every time I try to install Ubuntu or Kubuntu or ANYTHING, it does not work. Always either video card driver problems, or some apic or acpi problems, all these errors and only once have I ever gotten Ubuntu to install on one of the 5 systems I've tried on (all store bought systems), and even then it was with no nice effects because I had to use crappy onboard video. Now, I'm trying to recover files from my crashed Windows install, and again it won't work. So, PLEASE bear with me and listen to the details and hopefully help me solve my problem :P

Ok, so it installed, albeit in Safe Graphics Mode (nVidia 9800GT video card, should I have had to use safe graphics mode?) with the noapic option. That's lovely because I've so far tried Ubuntu 7.10, 9.10 and Kubuntu 9.10 and they all had problems (Kubuntu hanging at load screen).

Well, now when I boot it it loads up to the Ubuntu screen with the loading bar below it, then it loads the background and mouse pointer. All goes well until now, when I go to move the mouse and it doesn't move. Looking at the bottom of it, you can see the laser isn't even on, so the mouse isn't receiving power. Not only this, but the same thing is going on with the keyboard (different USB port, wireless receiver for the keyboard). This is where it stays, until the screen goes black from idling and it can't be woken up due to my having no way to cause any form of input. Not only this, but it doesn't appear to load anything apart from the background and pointer.

Also, when I unplug and re-plug in the mouse, the laser flashes on for a fraction of a second until it goes black again, as if the computer powers it, then realizes "Oh, its that mouse, stop powering that ****" and refuses connection. 

PLEASE help me, when I had Ubuntu working well, it was glorious. It's just so damned frustrating to try and work this that I'm soon going to give up on it all and just wipe the computer and reinstall windows, and wave goodbye to all my collection of stuff <_<

Edit: To add an interesting twist, I plugged my MP3 player in and lo and behold, it maintains a charging connection. Weird.

---

### Post by trixx on 2010-04-04
bumps...

I booted into recovery mode from Grub, and got these errors:

reiserfs superblock in block 16

usb 1-2: device not accepting address 2, error -110
usb 1-2:... same for 3, 4 and 5, then

hub 1-0:1.0: unable to enumerate usb device on port 2

Edit: also, I now get a 'mount of root filesystem failed' error now o.o

---

