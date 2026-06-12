---
title: "Ubuntu Netbook 10.04 on Kohjinsha SX3"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by Iwaki on 2010-08-10
I have tried several times to get Ubuntu to work on my SX3, and I gave it a serious attempt today to see if I could get things working, I'm getting a new hard drive so this is Ubuntu's last chance - for a while at least.

I've gotten past all the minor inconveniences and has it set up like I want it, but my problem is drivers. If I go to System - Drivers I get a grand list of 0 drivers on my system. Things like the touchpad, bluetooth and WLAN are working, but any function keys, brightness control keys etc are useless. In addition it either doesn't have, or is running on really bad drivers for my screen and graphic card. My screen comes up as "unknown" - though it's usable. Scrolling is not a matter of scrolling, but "jumping", and the computer is generally kinda sluggish (which is odd since it's running quite fine on Windows 7) and attempting to play any video file, on any media player - or even youtube - gives you a fps of about 0.1. (sound's working perfectly though)

I noticed some thread about laptops that are incompatible with Ubuntu somewhere, Is there anything that can be done about this or should I just give up and go back to Windows 7? Kohjinsha has drivers for XP, Vista, and 7, as a side-note, if it matters.

Thanks!

---

### Post by ajgreeny on 2010-08-10
Let's see the output from terminal of ```
lspci
```I suspect your graphics card is largely to blame, or the driver used for it at the moment, at any rate.

---

