---
title: "Kernel upgraded - lost floppy drive icon on desktop"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by epp on 2010-12-20
I have Xubuntu 10.04.1 LTS installed.  After the OS upgraded the kernel today from 2.6.32-26-generic to 2.6.32-27-generic and rebooted, the floppy drive icon disappeared from the Xubuntu desktop.

How do I get this back?

---

### Post by tommcd on 2010-12-20
> **epp said:**
> I have Xubuntu 10.04.1 LTS installed.  After the OS upgraded the kernel today from 2.6.32-26-generic to 2.6.32-27-generic and rebooted, the floppy drive icon disappeared from the Xubuntu desktop.

Just to be absolutely clear, this was a standard kernel update from the *standard* Ubuntu repos. Is that right?? Are you using any PPA repos or other sources for updated kernels??
What happens if you insert a floppy disc in the drive? Does it automount to the desktop?
If you go to XFCE settings > desktop > icons, be sure that *removable drives* is checked.

---

### Post by epp on 2010-12-20
Yes, standard update from Ubuntu repositories. 

I rebooted the system after this, selecting 2.6.32-26 from the menu and the icon reappeared on the desktop.  

I then rebooted one more time, the system did a file system check - then it rebooted again.  It went into 2.6.32-27 and the icon also appeared on the desktop for the first time using this kernel.

I checked the settings you specified, Removable Drives was checked.

---

### Post by tommcd on 2010-12-21
So the problem is fixed then?
If the floppy icon fails to appear again when you boot the system, it may be worthwhile to check that the floppy drive is seen in the computer's BIOS. Also insert a floppy disc into the drive and see if it mounts.
 If the floppy drive is buggy or failing, then that may explain why the icon does not show up on the desktop.

---

### Post by epp on 2010-12-22
On this particular system, yes, it seems to be fixed.

But on another desktop I have with the same installation (except that this system is dual-boot with Windows XP), the floppy icon has *never* appeared on the desktop since the original Xubuntu installation.

WinXP detects the floppy perfectly on this other system, so I know the floppy works and it is detected in the BIOS, but Xubuntu doesn't see it on this other system for some reason.  I also checked the same XFCE setting and Removable Drives is also checked.  I will boot this other system into Xubuntu later on and check if the floppy will mount on this other system.

---

