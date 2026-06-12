---
title: "New Natty VBox install - splash breaks login prompt"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by BkkBonanza on 2011-05-05
I just installed a test Natty VirtualBox server from the "mini" iso.

After doing that the normal boot always ends with a blank screen and cannot login. The recovery boot option does work normally. After much digging around and various tests I found that the "splash quiet" boot options cause this issue.

I removed them from the /etc/defaults/grub file and ran update-grub. Next boot the login screen came up after as normal. It seems when the splash  flashes that purple screen with the Ubuntu 11.04 message it is breaking something and does not get back out of some graphics mode.

This is in a VirtualBox window and I noticed that vesa framebuffers seem to be used by default in grub now. I never had this issue in previous releases and I'm just wondering if others have seen this and if there is a better fix than disabling splash. I don't mind having it disabled as this is a server install anyway and I'm fine with seeing debug messages during boot.

If other have seen this then perhaps it needs to be logged as a bug?

---

### Post by Icoo on 2011-05-21
Having the same problem...tried it over 3 times with the mini.iso and virtualbox, after install and restart it just sits there with a black screen. At least u got to grub I didn't even manage that...this sure is a problem...

---

