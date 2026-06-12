---
title: "no boot splash after new install"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by jej2003 on 2008-01-03
When I booted up using the livecd I got a nice boot scree showing me what was happening, but now for whatever reason I don't get anything but a blank screen.  I tried setting the video modes (vga=773 worked before but now does nothing but provide a blank screen again although the monitor seems to be adjusting its resolution bfore I get nothing).  What can I do to get the screen again?

---

### Post by jan quark on 2008-01-04
I solved this by using the alternate CD

When I installed via the Live CD the boot splash screen on my Ubuntu and Xubuntu box disappeared. 

but someone other have a clue how to solve this without a fresh install

---

### Post by perixx on 2008-01-04
maybe look here, if this applies to your problem:
[http://ubuntuforums.org/showthread.php?t=581075&highlight=long+booting+time]("http://ubuntuforums.org/showthread.php?t=581075&highlight=long+booting+time")
I've also encountered an issue with the live-CD for some weird reason activating the ANALOG/2nd video out of my graphics card at boot-up, instead of the digital out - or the switching of connectors during operation while graphics the mode is changed. 

I also have this problem under XP when loggin in, so it's maybe related to ATI cards/drivers...

perixx

---

### Post by jej2003 on 2008-01-04
I am using an onboard intel card in a dell dimension 2400, it's just wierd how the live cd detects it fine, but the install messes it up.  Anyway I change the resolution in usplash.conf to 1024x768 and that still didn't work.  Any other ideas?

---

### Post by jej2003 on 2008-01-05
This is the device information listed for my card btw
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by perixx on 2008-01-05
Sorry to hear that it's not working yet. Perhaps you can find a solution here, look for the hints on xorg.conf and the 'dpkg -reconfigure' method:
[http://ubuntuforums.org/showthread.php?t=658068]("http://ubuntuforums.org/showthread.php?t=658068")

perixx

---

### Post by jej2003 on 2008-01-05
I have gotten the boot splash to work, but I had to bump the resolution in usplash.conf down to 640x480 (which is fine).  I have seen similar issues to this with my model pc and graphics card, but I don't understand why this is the case.

---

### Post by perixx on 2008-01-05
good to hear you made it :)

---

