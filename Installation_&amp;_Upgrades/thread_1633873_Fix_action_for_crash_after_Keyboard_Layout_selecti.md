---
title: "Fix action for crash after Keyboard Layout selection in 9.04+"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by Rapture2k4 on 2010-11-29
Greetings,

I have had 4 netbooks. Asus 1005HA, and 3 Acer Aspire's. All 4 of these would crash when installing Ubuntu from either external CD drive or thumb drive. The crash would happen after you select the keyboard language/layout during the installer (even on the alternative install cd). I found that if you were to swap back and forth from AHCI to IDE in the BIOS enough times, it would finally get past this screen.

I ended up replacing the hard drives in the Acer netbooks, thinking they were having issues and then I noticed there is a dummy plastic insert in the CD card slot. I thought about it and then figured I'd remove it during the install and VIOLA!

I tested this on my tower with a USB card reader and the dummy insert. With the dummy card, it crashed in the same spot. The same thing happened on all 4 netbooks. I'm not a hardware guy, but I think maybe the catch/release mechanism might be the culprit. Is it hanging while it tries to read from a non-existant SD card, since it thinks one is plugged in.

I was pretty annoyed when I figured it out because I had spent well over 2 weeks trying to install a few different debian based distros. Maybe something to look into and/or try if you are having issues.

Regards,
Rapture

---

### Post by mörgæs on 2010-11-30
Thanks. Does this also apply to 10.10? 

If so, do you feel like adding your findings to
[www.linuxhcl.com](www.linuxhcl.com)
?

---

