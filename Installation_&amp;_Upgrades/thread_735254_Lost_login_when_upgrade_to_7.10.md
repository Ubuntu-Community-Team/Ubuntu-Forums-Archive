---
title: "Lost login when upgrade to 7.10"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by chastom on 2008-03-25
I upgraded from 7.04 to 7.10 via update manager and now my machine boots to a blank brown screen with no logon promp.  When I boot to the recovery option, the check sequence ends with the statement "init: rcS-sulogin main process (4351) terminated with status (127), when I type "exit".

Now I can not get into Ubuntu.

---

### Post by dstew on 2008-03-25
They really should take that option out of the Update Manager. It often fails to work. At this point, in my opinion, you should boot a Live CD, back up your home folder to a USB drive, and do a fresh install.

---

### Post by chastom on 2008-03-25
I was afraid that might be the only option.  I dual boot Ubuntu and windows xp on my laptop so it may be more of a major mess than I am up to right now.  I got into Ubuntu 7.10 by using startx at the grub recovery option prompt, but that was of no value to my level of experience. I tried  "sudo dpkg-reconfigure gdm" via the terminal while in x but it failed.  

Thanks for reading my problem. I'm going to format the hard drive and drop out of Ubuntu for now. Too much work cleaning up upgrades.

Dell 5150  PIII

---

