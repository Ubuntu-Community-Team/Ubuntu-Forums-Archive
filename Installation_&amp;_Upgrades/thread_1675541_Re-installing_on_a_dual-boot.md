---
title: "Re-installing on a dual-boot"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by groping_blindly on 2011-01-25
Hey all,

Anyone know about re-installing 10.10 on a dual boot?  

I recently set up a W7/Ubuntu 10.10 dual boot on my new pc, and did so by installing W7 first with about eighty percent of the 1TB drive allocated to it.  After that, the Ubuntu boot CD found the unallocated portion no trouble and comfortably installed on the rest, so I'm assuming the Ubuntu disc is ok.  

All was well until later when I tried to install the propriety ATI drivers for my Radeon 6850 in Ubuntu.  Now, the Ubuntu install has gone irreparably apeshit. This is my first time using 10.10, and my top tip for Ubuntu is still never under ANY CIRCUMSTANCES use the hardware drivers utility under the sytem->admin menu (I think it's called 'Jockey'?)  It's still a worthless piece of ****.

Now for the hard part:  When I try to re-install Ubuntu from the CD, it crashes spectacularly with screens full of coloured flashing error messages on pink background no less, and I'm guessing this is because there's no unallocated drive space to install it to and it's getting confused by the W7 install.  I can't see the ext4 partition from inside W7, and even from a recovery-mode boot, Ubuntu is hopelessly erratic and broken right now, so I don't think I can delete the Ubuntu install from inside Ubuntu (maybe?).  

Any ideas on how to move along?  All I can think of is to buy a new HD and start all over again.

---

### Post by kansasnoob on 2011-01-26
At what point does the live CD "crashes spectacularly with screens full of coloured flashing error messages on pink background no less"?

Are you not able to even run it in live mode?

I'd begin by booting the live CD and just after the system/BIOS screen passes you'll see the purple screen with two small emblems at the bottom. You then have three seconds to press any key (I usually hit Enter), then you'll see a screen to select language. After that you'll see a list of options.

Select "Check disc for defects" and allow it to run for a few minutes. It should return a message saying no errors were found. If the disc checks OK then look here:

[http://ubuntuforums.org/showthread.php?p=10373780](http://ubuntuforums.org/showthread.php?p=10373780)

It appears to me that gpu is just not well supported ATM :(

---

