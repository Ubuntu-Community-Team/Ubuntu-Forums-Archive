---
title: "Unexplained periodic boot failures"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by raj727 on 2007-08-27
I've experienced boot failures while using 7.04.

My computer hangs after choosing 7.04 in the GRUB menu.  I had just gone through the detailed 30 day forced systems check, went into Ubuntu and then shut down my computer.  When I tried to boot the next day, my computer hung very soon after the Ubuntu start-up graphics appeared.  The bar was lit up less than 5% across.  I waited several minutes and noticed the hard drive light was also not on.  I attempted another15 boots with the same results.  During these attempts, I also tried the control+alt+F4 command after leaving the GRUB menu but the computer still hung.  Someone had suggested trying this previously and it seemed to work after going through a text based boot-up process.  This time no such luck.

Since I had a dual boot setup, I tried to boot up Windows XP X64 from the GRUB menu and was successful going into Windows.  This indicated to me that my hardware was operating correctly.  I then tried to boot up Ubuntu using a liveCD, but my computer continued to hang early in the bootup process.  I tried booting with s liveCD 3 times with the same results.  I then did a memtest just to see if it would reveal anything.  After going through the memtest for about 2 and 1/2 hours and not finding any errors, I quit the memtest.

I then tried to boot again from the GRUB menu and for some reason, this time, I was successful.  It has now booted successfully three times.

I had this same problem about two months ago and only booted after 10 to 15 boot attempts.  I thought it worked because I used the control+alt+F4 key during the bootup process but I now think it worked only after a certain number of boot attempts.

I've writing in case others have had the same problem and to see if I can do something when it happens again.  Would it be an idea to refer this problem to Ubuntu?

---

### Post by Pumalite on 2007-08-27
Try rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) and investigate your system. If nothing is wrong, post a bug in launchpad.

---

