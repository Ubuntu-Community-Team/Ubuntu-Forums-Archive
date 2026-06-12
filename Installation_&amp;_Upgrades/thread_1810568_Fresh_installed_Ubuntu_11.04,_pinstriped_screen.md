---
title: "Fresh installed Ubuntu 11.04, pinstriped screen"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by Ck.asdf on 2011-07-23
I fresh installed Ubuntu 11.04 twice now, on two different hard drives, and both times, I have gotten an annoying problem.  When the system boots up, it ends at what I assume is the login screen, except the whole screen is covered in narrow vertical black & white stripes.  The mouse is in front of these stripes, but nothing I do gets me past them.  If I press ctrl + alt + Fn to get to a TTY, it shows a black screen.

I have found somewhat of a workaround - I first boot to the recovery mode, which shows a messed up screen, then I boot to the normal mode, and it works.  Not sure how this has an effect, but as soon as I turn it off again, it's back to not working.

You can see the attached files to see what I mean.  Any suggestions on what can be done to fix this?

As far as hardware goes, this computer has whatever Intel graphics card that the Lenovo L420 comes with.

Thanks for any help you might give! :)

---

### Post by 2F4U on 2011-07-23
There seems to be a bug report that matches your problem description

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777212](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777212)

It contains a workaround that involves adding some parameters to the grub configuration.

---

### Post by Ck.asdf on 2011-07-24
Thanks 2f4u, I tried that, we'll see what happens upon reboot.  I appreciate you pointing that out! :)

---

### Post by rokob on 2011-07-27
I had the same issue with my L420. I solved it with the advice given in [http://ubuntuforums.org/showthread.php?t=1769672](http://ubuntuforums.org/showthread.php?t=1769672), basically I made my grub file look something like:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="" 
GRUB_GFXPAYLOAD_LINUX=1360x768x60

---

### Post by Ck.asdf on 2011-07-27
2F4U, the solution you linked to worked well! Thanks again!

Also, glad to hear there's also another workaround, rokob, for those who may need that solution.  I wonder what the differences are in the two different solutions?

---

