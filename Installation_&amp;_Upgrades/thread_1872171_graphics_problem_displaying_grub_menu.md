---
title: "graphics problem displaying grub menu?"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by smaring on 2011-10-30
I have a laptop with the dreaded Intel 5100 AGN wireless card.  It did not take well to the 11.10 upgrade.  I have been advised that my only hope, for now, is to downgrade the kernel to 2.6.32.x.  I have installed the kernel, and I see it as an option in the /boot/grub/menu.lst.  However, I don't ever see the grub menu during boot!

My timeout is 10, and I have commented out "hiddenmenu" and the "defoptions" of "quiet splash".  I can tell that it waits about 10 seconds before selecting the default, which is the default 3.0.x kernel, but I would like to actually see the menu, and select the older kernel.  Pressing "esc" or holding down "shift" during the process does nothing.

So, short of changing the "default" integer to the menu choice I want and updating grub, are there any thoughts on why I get a blank screen and no errors?  Is it, perhaps, picking some fancy frame buffer format that my video card does not like?  Is there a safe default to give me a simple console based menu?

This takes me back to the good 'ole days of Slackware, where one problem led to another, to another, and yet another, and by the time you knocked out a handful of 'em, you completely forgot what you were trying to do to begin with!   LOL

Thanks,
Steve Maring
Tampa, FL

---

### Post by smaring on 2011-10-30
I don't think grub was installed properly.

I did a "grub-install --recheck /dev/sda" and I can now see the menu and make my selections.

---

