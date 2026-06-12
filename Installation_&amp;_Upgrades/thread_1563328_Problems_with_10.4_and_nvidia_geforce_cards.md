---
title: "Problems with 10.4 and nvidia geforce cards"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by wjhildreth on 2010-08-28
I upgraded an Ubuntu 9.4 machine to 9.10.  This machine is dedicated to running Boxee.tv.

The upgrade seemed to go fine, until the reboot.  When the machine re-booted all the monitor tells me there is no input signal.  I tried using the nomodeset and xforcevesa in grub, but it still does not work.

Next I thought I would try a fresh install of 10.4.  When the machine boots from the disk, you will few seconds of the splash screen and then the same problem.

I have tried with both a Nvidia Geforce fx 5200 (128mb) card and a Nvidia Geforce fx550 (256mb) with the same results.

The install works fine with the onboard video controller.  The problem is, the onboard controller is JUNK.

Any ideas how I can get 10.4 to work with any of these cards?

Regards,

Joe

---

### Post by wjhildreth on 2010-08-29
Just an update.

I downloaded the alternate cd and tried tp install from that.  The install and reboot went well.  I ran the updates and installed the restricted nvidia drivers,  On reboot, I had a black screen again.

I booted from the Alternate cd and selected repair from the menu.  I mounted the root partition and edited the xorg.conf according to this post

[http://ohioloco.ubuntuforums.org/showthread.php?p=9777692]("http://ohioloco.ubuntuforums.org/showthread.php?p=9777692")

after saving the changes and rebooting, I am able to log into the desktop again.  I hope that helps someone.

Regards,

Joe

---

