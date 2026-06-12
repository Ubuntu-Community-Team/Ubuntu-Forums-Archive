---
title: "Replace Chrome OS with Linux on Chromebook"
date: 2018-04-02
forum: Installation &amp; Upgrades
---

### Post by sduverge on 2018-04-02
Well, I've been using crouton now for about a year to run Xubuntu on my Chromebook.
Today I got the end of support message, meaning my device won't receive more updates. *Programmed obsolesce*
So I'm ready to do the full change, and though I've been an Ubuntu user for years, I've never dealt with fully integrated hardware, so I need some guides.
I'd like to install Ubuntu as a fixed OS.

Device is HP Chromebook 14 c050nr
1.1 GhZ Intel Processor
4GB DDR3 RAM
16GB SSD

Thanks in Advance.

---

### Post by TheFu on 2018-04-02
Every chromebook module seems to be a little different, so you should find a how-to guide for your specific version.  My knowledge from my Acer C720 and Toshiba CC3550 won't help. Sorry.  Almost all of these systems will require removing the hardware lock, going into "developer mode" in chromeos, putting in a different BIOS, before loading any Linux.  Doing this means that running ChromeOS won't be possible again on the machine.  I think some models allow flashing back the original firmware, putting the hardware lock back (somehow) and re-installing the factory chromeOS ... mine do not.

BTW, if it has an SSD, now might be a good time to swap in a larger one.

---

### Post by sduverge on 2018-04-02
I already go into developter mode so I can boot crouton, but in this case, I'm running linux inside chrome OS, like a VM. I wouldn't mind not being able to go back to chrome OS since they've notified they won't continue to update and support this computer model.

---

### Post by TheFu on 2018-04-02
Crouton is a chroot technique, actually.  Very different from running a VM, especially from an isolation standpoint. I used crouton a little.  Every time google pushed out a new OS version, crouton would break.  They did it just before I was going on an overseas trip, which really annoyed me.  Plus, not being able to delay the download sucked.

I think there are good guides for your type of chromebook.  Shouldn't be too bad.

---

