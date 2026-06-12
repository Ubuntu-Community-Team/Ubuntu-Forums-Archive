---
title: "GRUB Error 21"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by KFirth31 on 2005-06-29
Ok, first I will explain how my computer is set up.  On my primary drive I have Windows installed and I tried to install ubuntu on my slave drive.  The entire installation goes fine until I get to the point where the computer restarts and tries to use GRUB.  I then get an error 21 and cannot find a way to fix the problem.  Also, on one of the last stages of the installation where it shows what operating systems are detected, Windows is on the list.  Any help with this would be appreciated.

---

### Post by skoal on 2005-06-29
Well, this problem might fall under several scenarios.  Without you posting your /boot/grub/menu.lst file here, I'm only speculating.  However, the quick and easy fix might be this:

In your BIOS, change hda to use "mode = LBA" if it was set to "auto", if Windows is on drive a and that's where you installed grub to.  You might have to change the "type" setting to "user" in order to get that option.  And (assuming) drive B (or on a second IDE port with another drive letter) is where you installed Ubuntu to, leave that one set to "auto".

\\//_

---

