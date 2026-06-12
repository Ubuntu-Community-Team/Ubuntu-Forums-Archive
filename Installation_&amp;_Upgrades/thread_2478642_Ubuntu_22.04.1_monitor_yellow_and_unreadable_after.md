---
title: "Ubuntu 22.04.1 monitor yellow and unreadable after Try or Install screen"
date: 2022-08-31
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2022-08-31
I'm using a bootable USB with Ubuntu 22.04.1 (just updated to the August release to see if that would fix the problem - it doesn't).

When I boot from the USB, I can see the Jellyfish splash screen and then the Try or Install screen.  If I choose Try, the monitor turns into yellow with some impossible to read icons.  If reboot, choose Safe Graphics, the monitor is usable after Try.

The machine is a Dell XPS 8950 with Windows 11, with NVidia GeForce RTX 3060 T1.  That's what seems to be causing the problem.   When I tried the bootable USB on a laptop with Intel UHD video, it works fine (although the laptop is about to go back to Dell for diagnosis and repair - ironically).  I'm not ready to actually install Ubuntu 22.04.1 yet, but I'd like to continue playing with the bootable USB. without installing.

How can I install the NVidia driver on the USB, and have it still capable of running on computers with different video hardware?  I can't make much sense of what I'm finding.  And I'm also not sure that I'm using Rufus correctly.

Thanks!

---

### Post by Impavidus on 2022-08-31
You can't. It's one of the limitations of a live usb.

---

### Post by MAFoElffen on 2022-08-31
On boot... press the left shift key to try to get the grub menu to show... (You may biot have to do the previous, since you are dual boot) At the grub menu, press the <E> key to get into an edit mode... <Arrow-Down> until you get to the line that starts with the word "linux'. <Right-Arrow> until you get past the "--". Add "nomodeset".

Press <Cntrl><X> to boot.

After it boots, go to Software & Updates > Alternate Drivers and install your nvidia driver...

What is going on that applys to your Dell Warranty? Since I was an Onsite Warranty Tech for Dell, I'm curious...

---

### Post by 5circles on 2022-08-31
Thanks @Impavidus and @MAFoElfen.  I may not get a a chance to look further until after Labor Day - I'm already way behind getting ready.

@MAFoElfen:
1. Would you describe using a Bootable USB as dual boot?  Just curious, that's not how I think of it.
2. The machine that's going back is an Inspiron 7573 two-in-one.  It is a couple of years old, and I neglected to really get into support with Dell because there was so much going on (various things related to moving house for an entire year- more really of the aftermath).  The machine started off working very well, and was that way for at least a year - running virtualization with  Ubuntu in a virtual machine for development purposes.  I don't think it was dual boot.  When things started going wrong, I chose to get a new laptop instead of fixing - in part because I usually have a main and a fallback.  What was happening was extremely slow performance for a long time after boot, and then just slow, plus the laptop keyboard misbehaving (perhaps also other keyboards directly connected) - keys struck and not recognized (sometimes different between upper and lower case), key strikes generating multiple characters; but nothing showing up with diagnostics. When I started down the path with Dell support, I'd already decided that I would need to do a complete system rebuild.  I started down that path before calling Dell, and got into an endless Restart / Reinstall loop.  Dell support tried pretty much the same as me, with a new USB recovery drive, and ultimately decided to have me send the laptop in.
3. The eventual goal with the XPS 8950 is a machine with a vestigial Windows 11 system, Windows 10 virtual, Ubuntu virtual - perhaps more than one if I need to access multiple MySQL instances as recommended on this forum.
4. I just bought a USB-C to VGA/HDMI adapter.  It works fine on the laptop that's going to Dell, but the XPS 8950 doesn't recognize it through either USB-C connector.  I've tried a Windows tool, can't see much on Ubuntu without installing something.  So that might be another call to Dell.  Sigh.

---

