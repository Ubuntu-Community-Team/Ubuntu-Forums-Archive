---
title: "I can not get ubuntu to boot"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by kgwurth on 2008-01-04
Hi,

I have tested out the live CD on my system (HP with Radeon X1650 video card).
The live CD booted and ran with no problems.  

However when I install on my Drive and attempt to boot I get a message saying it is loading (boot manager).  The display then goes blank, I see my hard drive being hit and my CD drive being hit. That all settles down and the display remains blank.

I have tried booting in recovery mood and it gets to a  prompt but I don't know enough to go from there.

Can anyone please help?

Thanks for your assistance

Karl Wurth

---

### Post by Casual Fan on 2008-01-04
Try this...reboot and when grub comes up, press ESC.
Select your kernel...probably the one with the highest number that's not a recovery mode...and press e.
Then select the line that begins with "kernel" and press e.
Go to the end of the line and delete "splash." Then press enter, and press b.

It should boot fine, but with all of the system information scrolling down the screen. It's some kind of bug that I experienced with Gutsy. Your computer would have probably booted eventually; it would have just taken a long time. It took me 2-3 minutes as opposed to about 75 seconds with this fix.

When you get into Gutsy, you can download Startup Manager from the Applications menu, and tell it to not display the splash screen, and bypass that bug permanently. (I don't think the GRUB fix is permanent.) It just won't look as pretty.

I hope this works...

---

### Post by kgwurth on 2008-01-04
Thanks for the info.

I am trying that now

Karl Wurth

---

### Post by kgwurth on 2008-01-04
Just wanted to let you know that fix worked.

Appreciate your help

Karl Wurth

---

