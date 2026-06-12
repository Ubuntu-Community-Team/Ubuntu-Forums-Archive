---
title: "Can't boot from new installation on SSD"
date: 2016-01-16
forum: Installation &amp; Upgrades
---

### Post by dcroxton on 2016-01-16
Recently I was having problems with my old hard drive, so I bought a new SSD and installed Xubuntu 15.10 onto it.  Since my computer wasn't working, I created a boot cd from windows, plugged in my SSD through a SATA-to-USB caddy, and installed Ubuntu onto it that way.  The installation seemed to go fine, but when I plug the SSD into my computer, it isn't recognized as a boot device  Well, the BIOS recognizes it as a boot option (actually at least two, UEFI and normal), but whichever I try to boot as, it just says, "Insert boot media and restart."

I am totally baffled why this is happening.  I can only guess that there is some new technology that I'm not aware of that requires a different boot setup.  I do have a new motherboard, but it boots my old SSD (which works sporadically) and an external DVD okay.  I have fiddled with the settings for UEFI vs. legacy, and some other boot device setting that mentions legacy vs. some alternative, but nothing has worked, and frankly I'm at the end of my rope.  I would be grateful for any suggestions.

---

### Post by Bucky Ball on 2016-01-17
Have you tried [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")? Are you dual-booting with Win on that drive, or any drive? If so, did you install to the hard drive in BIOS or UEFI mode?

If you have Windows installed in UEFI mode and Ubuntu in BIOS there _will_ be problems.

---

