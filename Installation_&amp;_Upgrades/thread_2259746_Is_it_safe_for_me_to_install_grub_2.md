---
title: "Is it safe for me to install grub 2?"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by chcwebb on 2015-01-06
I installed Ubuntu alongside Windows 7 a couple years ago on my Asus laptop (I think I used wubi, but can't remember), and at some point in version 12 it stopped booting - I could select Ubuntu in Grub but received some sort of error which I now forget.  I never got around to fixing it, and just used Windows 7 for a while.  Recently, my computer abruptly lost power and my antivirus stopped working - AVG said all components were off and the AVG controls crashed when opened.  I figured it was due to the power failure, but in case it was a virus I backed up my files and didn't want to touch the internet.  So I tried booting Ubuntu, and all of a sudden it worked!  I suppose a Windows update messed with the boot, and then that was later fixed?  I decide to catch up on updates, and it asks to upgrade to version 14.  I go ahead and go for it, but then after I upgrade Ubuntu stopped booting, giving me a no init error instead.  I find out that this can be fixed with Grub 2, but I only have Grub.  I thought maybe I could install another Ubuntu on another partition, and try to set up a usb drive to install Ubuntu, but when I install the USP software it edits the BIOS and I stopped even seeing the Grub screen.  I figured at that point I should start from scratch rather than continuing to break things, so I do a Windows factory reset.  

I have two hard drives, so my old Ubuntu install should still be intact, and I want to get it back.  I suspect that I could install Grub 2 from Windows 7, see the old Ubuntu install, fix the no init error in Grub 2, and move on with my life, but I'm worried that I'm just going to make things worse.  Is this the right idea?

---

### Post by TheFu on 2015-01-06
You are all over the place and lost me.

If you seek 100% assurances that installing a new boot loader won't have issues, then you need to look elsewhere. There are no guarantees.

If you used WUBI, there is little support anymore. It is deprecated and will not be supported in the future.

Perhaps running **boot-repair** is the easiest method to try first. At a minimum, data about your setup will be captured and you can provide a link to it here. At the best, it will fix whatever boot issue there is.  See my signature for links to instructions for the tool.

---

