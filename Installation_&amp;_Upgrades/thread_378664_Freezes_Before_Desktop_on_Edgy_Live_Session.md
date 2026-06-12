---
title: "Freezes Before Desktop on Edgy Live Session"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by hiker13526 on 2007-03-07
I originally tried the default option on the live cd (desktop amd64) and it would boot normally until it began to display the gnome session. Before the normal loading desktop screen comes up, my lcd screen popped up saying mode not supported. Then I figured I best try a different mode than the plain vga, so I set it to 1024 x 768 with 16 depth. I then received green/yellow/black vertical lines across my screen. These problems occur AFTER the little ubuntu loading bar is finished. I then set the color depth to 32, and what would come up then is a light beige, similar to the reply to button links on these forums or the color of the farthest left on the banner for these forums. That would be all I would see across my whole screen and it would freeze. Numlock didn't respond, so I waited about 10 minutes and declared it DOA.

After all this I searched the forum and read about noacpi commands. I entered all I could find to no avail. I also tried the nodma command, nothing. Then I read about trying dpkg-reconfigure xserver-xorg. If I hit CTRL - F1 when I got the green lines/video mode not supported/beige screen and I typed REALLY fast, I was just barely able to begin reconfiguring the video before my entire pc froze. Completely unresponsive, and I only got this far if I typed the sudo dpkg-reconfigure xserver-xorg command REALLY fast. Otherwise it would freeze and CTRL F1 would do nothing.

Ran mem test, cd check, burnt at 1x, used the verify cd in nero, md5 sum checks out, tried burning from 2 different computers  with different burner brands and media brands, tried nodma commands, noacpi commands, tried removing all non-essential devices (usb printer, flash drive, scanner, tv card, extra cd rom drives, and ALL my hard drives (just to get something...)). Nothing seems to work. I am beginning to think I wasn't meant for linux.

**_Machine Stats:_**
Windows XP SP2 - working fine so far
*1 x AMD 3200+ 64 bit CPU
*1 x Foxconn NF4K8AB motherboard
*2 x 512 mb RAM sticks
*1 x Samsung DVD Reader
1 x MAD DOG DVD Burner
1 x WD Sata Drive
2 x WD IDE Drives
*1 x eVga Nvidia 6800 GS pciex card
1 x ATi TV Wonder VE pci card
*Mouse and keyboard are ps2
*MAG LCD monitor is vga and I can run at 16/32 640/800/1024/1280 on Windows.
Currently using 32 depth with 1280x1024.


I put *'s next to the "essentials". That is, I tried booting with JUST those things and it didn't work.


Help? :'(

---

### Post by wpshooter on 2007-03-07
Did you test the CD integrity by running the verification function that is found on the initial Ubuntu boot screen menu ?

Did you try booting using the safe video mode parameter ?

Have you considered trying the 32bit version ?

Have you considered trying the ALTERNATE CD version instead of the DESKTOP (live) CD version ?

Good luck.

---

### Post by hiker13526 on 2007-03-07
I did verify it from within the ubuntu boot screen menu.

I tried using the default safe mode option on the boot screen, but I haven't tried a different command line parameter. What is the safe mode option?

I tried the 32 bit version and I believe it was purple lines I would see instead of green lines. Not much of an improvement =/

I don't feel safe trying an alternative install because thus far it seems as though I'd get the same problem on my first boot into ubuntu...

---

### Post by hiker13526 on 2007-03-08
If anyone has any other recommendations, I'd love to know what they are...

---

### Post by hiker13526 on 2007-03-11
I just tried each memory stick individually, no better results. I then tried a new power supply, same problem.

I noticed errors like this showing up during boot, but before the screen turns solid beige:
```
hda: command error: status=0x51 { DriveReady SeekComplete Error}
hda: command error: error=0x54 {AbortedCommand LastFailedSense=0x05
ide: failed opcode was: unknown
end_request: I/O error, dev/hda, sector 1430256
Buffer I/O error on device hda, logical block 357564
```

As a note, hda is NOT a hard drive. I believe it is my cdrom, but I could be wrong. When these errors appear, I had no hard drive plugged in.

---

