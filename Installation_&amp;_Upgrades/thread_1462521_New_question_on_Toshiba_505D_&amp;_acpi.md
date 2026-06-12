---
title: "New question on Toshiba 505D &amp; acpi"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by rdingraham on 2010-04-25
I have read some of the posts on this problem by colinwhipple and Linux_Lurker, so I decided to go ahead and try to install 10.4 on my Toshiba Satellite.

The only way I could get it to install was to use acpi=off.  I did this (from the live CD) and the installation seemed to complete smoothly.  However, now when I boot up from the hard drive, the screen goes directly to a line of text error messages, exactly the same as I got previously when trying to install with acpi active ( see thread [http://ubuntuforums.org/showthread.php?t=1460445&highlight=ingraham](http://ubuntuforums.org/showthread.php?t=1460445&highlight=ingraham) ). 

I know that before I make any advanced changes I will have to get into the Grub menu.lst file and add the parameters for acpi=off (or one of Linux_lurker's other suggestions.

How do I do this?

If I boot from the hard drive, it just takes me to the screen of error messages.  I never get to the Grub menu, and I have no option to boot into terminal

If I boot from the LiveCD, I can see my hard drive in Nautilus, but there is no menu.lst file in the Grub directory.

Pressing "e" while the computer is booting does nothing.

I can't figure it out. Please help.

Bob Ingraham

---

### Post by rdingraham on 2010-04-26
After digging around on the web, it seems to be the case that Ubuntu 10.4 uses Grub2 which has eliminated the menu.lst file, and instead uses the file boot/grub/grub.cfg.  So it appears there is no menu.lst to edit.

I booted the LiveCD (with acpi=off), located this file on my toshiba hard drive, but have no idea what to do next.

Still waiting for help.

Bob Ingraham

---

