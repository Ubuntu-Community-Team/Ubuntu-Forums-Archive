---
title: "Installing 10.10 64bit out of a working 32bit version"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by fopbot on 2011-01-11
So I tried to install the 10.10 64bit version on my new laptop, only to be fooled by a "ready when you are" message and aborting the installation.
Inspecting what has been written to the disk, I can say that installation was nearly complete, but it can't boot from there because the initrd file is nowhere to be found.

I have a working 32bit version running on the laptop right now and was wondering if there is a simpler way to install the 64bit version out of running 32bit session (since that would be much more comfortable than checking the cd image, redownloading, reburning, rebooting, etc. etc.)

Can I get the standard initrd for 64bit systems from somewhere to make the system boot-able?
(can't really find anything on the install cd-rom)
Also generating it while running 32bit seems not feasible, or does that even matter for that file?

Or: Is there an easy way to execute the installation process out of my running session, although it is for a different architecture?

Thanks

---

### Post by West201 on 2011-01-11
look at this thread [http://ubuntuforums.org/showthread.php?t=118538](http://ubuntuforums.org/showthread.php?t=118538)

---

### Post by dino99 on 2011-01-11
the generic-pae kernel will offer the 64 bits advantages on a 32 bits system, with less trouble :)

---

### Post by fopbot on 2011-01-11
Thank you both for your suggestions.

The easiest way was to just reinstall again. No shortcuts. No trouble.
Everything works perfectly now.

---

