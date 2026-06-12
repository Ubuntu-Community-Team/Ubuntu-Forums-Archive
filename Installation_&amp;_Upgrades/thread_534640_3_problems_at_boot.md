---
title: "3 problems at boot"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by thinsoldier on 2007-08-25
haven't been able to boot ubuntu since some time in January and can't find anyone in my area to pay to fix it :(

I had Ubuntu and Windows dual booting properly

hd1 just has windows xp
hd2 has no os
hd3 has 2 partitions: 1 fat32 and the other was ubuntu.

I was experimenting to see if I could start a download in windows, save it on hd3, reboot to Ubuntu and finish it. It seemed to work for ftp, firefox, Azureus.

A few weeks later when I try to boot Ubuntu again it always says "scanning file system" and I have to wait about 4 hours while it scans the fat32 partition on hd3. I don't know if it ever finishes the scan, I just see the screen go black. And no it's not a timed function of my monitor to turn off after a few hours. I hooked the monitor up to the laptop and back to the ubuntu machine to make sure.

Anyway. Today I deleted every file on the fat32 partition of hd3 that was over 10 megs and tried booting ubuntu again.
The file system scan finished in under a minute and then I got a message displayed by Xserver that kept being interrupted by the command line still trying to display something so it's like a visual glitch where I'm supposed to be looking at a full screen error message but the command line keeps trying to scroll underneath it.

The full screen message says: Failed to start Xserver. and then are various yes no options to view more and more detailed error reports about X and finally the last part of the message is:
The X Server is now disabled. Restart GDM when configured correctly.

And while trying to read all this I get interruped by the command line saying:
78.649752] hdd: drive not ready for command
78.649752] hdd: drive not ready for command
78.649752] hdd: drive not ready for command
78.649752] hdd: drive not ready for command
78.649752] hdd: drive not ready for command
78.649752] hdd: drive not ready for command
78.649752] hdd: drive not ready for command
78.649752] hdd: drive not ready for command
78.649752] hdd: drive not ready for command
78.649752] hdd: drive not ready for command
78.649752] hdd: drive not ready for command
......x infinity

What am I supposed to do?

---

### Post by Pumalite on 2007-08-25
Start with the xserver. At the command line: sudo dpkg-reconfigure xserver-xorg. Accept most defaults, choose 'vesa' as your driver, the: startx. Come back later for the rest. Let's see how this goes first.

---

### Post by thinsoldier on 2007-08-25
:) worked

And didn't get the hdd: drive not ready error
Maybe my drive is acting up randomly?

what the heck does GDM stand for?
And can you give me a definitive convincing answer as to whether or not it's save to write files to a ntfs partition from Ubuntu and how to activate this functionality.

What I'd like to do is put my windows xp desktop and storage folders on the 2nd storage drive and also somehow move my linux desktop and storage folders onto that same drive so that I have access to everything I need no matter which OS I'm using.

---

### Post by merlinus on 2007-08-25
It is a problem with the correct driver for your video card.  Try searching for it.

GDM = Gnome Desktop Manager.

-merlin

---

### Post by Pumalite on 2007-08-25
It's possible you need a 'Legacy' driver. For the rest; you need ntfs-3g installed through Synaptic. And yes, it is safe.

---

### Post by thinsoldier on 2007-08-25
Internal Error: Failed to initialize HAL
what is that?


I fixed my Beryl Problem.

I've marked the ntfs-3g package for installation in synaptic...now...how to I actually Install it?

---

