---
title: "[SOLVED] grub changes after boot"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by revtds on 2008-08-28
Three weeks into a clean install of ubuntu HH, on an AMD AThlon 1G, 1G RAM, ATIRadeon 7200 that had been running Kubuntu well, but which I could not make networking or PDA syncing work, I have had an ongoing problem that I cannot find reference to in the forums.

When I rebooted after the initial install, I got "error parsing number" from Grub and no boot. Running off a live CD, I read up on HH using scsi drivers for ide drives due to better performance.  When I changed Grub lines from "sd0" back to "hd0" it booted and everything was fine. Finished configuring desktop etc., ran for a week with no problems and when the Linux headers came through as an update, I installed with Update Manager, rebooted and was again told it couldn't parse its numbers.  Changed Grub again, OK.

I have now had to reboot six other times for various and sundry reasons, all of my choosing, and every time Grub has changed back to "sd0" instead of "hd0".

Why does it do this and how do I stop it?

Any help would be greatly appreciated.

---

### Post by revtds on 2008-10-17
I discovered that when I edited grub while in grub, none of the changes effected the grub menu.lst.  Editing menu.lst with gedit took care of the problem.

---

