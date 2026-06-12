---
title: "Aspire One USB Boot Intel PineView Message"
date: 2012-03-11
forum: Installation &amp; Upgrades
---

### Post by OldAndTired on 2012-03-11
An earlier user had this (edited), as do I:

                                  **BIOS won't install Ubuntu from USB (Acer Aspire Netbook)**             
                                                                I'm almost  completely new to Ubuntu.  I wanted to  install it onto  my netbook instead of Windows 7 Starter, but I can't  get things to work.

Here's my situation:
Acer Aspire netbook

I put Ubuntu on a USB stick with UNetbootin.  Other posts reference Netbook Edition; that didn't appear to be an option with UNetbootin. 

Once I boot from USB I get s short syslinux 4.03-message, and then a  black screen reading Intel(r) PineView PCI Accelerated SVGA BIOS Build  Number: 1818 PC 14.34 etc. etc. Everything stops right there.

The USB worked ok on my antique Thinkpad.

So: Screen resolution?  Processor type?  Something else?

Thanks for any help you can provide!

---

### Post by OldAndTired on 2012-03-11
Me again.  Logging in case a future victim gets here.  In BIOS Setup Main I disabled Quick Boot and enabled F12 Boot Menu.  This had no effect.

Post [http://ubuntuforums.org/showthread.php?t=1652723](http://ubuntuforums.org/showthread.php?t=1652723) states "The bios will not tolerate the current or earlier syslinux versions, and  always hangs with that stupid message. It seems not possible to make a  bootable USB flash drive using the current syslinux. This seems to be a  deliberate mechanism implented within the bios."  Gee, I hope not.

---

### Post by OldAndTired on 2012-03-11
As a further update, a little research shows that to get other Acer models to work you have to enable booting from USB in the BIOS.  There is no such option on my Aspire One.

---

### Post by OldAndTired on 2012-03-12
So, when I posted to a closed thread I got a response within 30 minutes; oh well.

---

### Post by dxk on 2012-06-30
Hello, I had the same trouble while trying to install Lubuntu 12.04 on my emachine em350. I was trying to install it from a 4 gb Kingston Data Traveler 112. Didn't work and tried to search for help without any luck. Then just decided to install with my other USB, an 8 gb Kingston Data Traveler 102 and it worked. I'm running Lubuntu right now. So just try to switch to a newer USB. Not sure if you already found out a solution, but just wanted to post this here.

---

### Post by waxcan on 2012-11-25
Thanks, I've got the same problem with my em350, trying to boot backtrack loaded on a generic 4gb drive of some type. I bought a new 16gb USB and I'll post here once it arrives and I try it out.

---

