---
title: "boot-repair fail after upgrade from 12.04 to 12.10"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by hazmat74 on 2013-04-01
Hello,
I have instability issues after recent upgrades (I don't know which ones might be responsible) in 12.04. I've checked my memory with memtest86+, scanned the hard disk, and checked for other possible hardware issues with lm-sensors. Nothing has come up. The failures seem to be related to graphics, but I'm not sure how. Compiz was crashing frequently, so I ran Ubuntu 2D hoping for some stability. That helped in the sense that X didn't fail completely. When the computer crashes some programs may still be up and running like firefox, but it isn't possible to do anything else at all. I don't think this is a hardware issue, because memtest86+ ran all night without any difficulty. When Ubuntu is running, the OS crashes somewhere just over 50 minutes with regularity, whether or not I'm logged into the Ubuntu desktop. Updating the kernel from 3.2 to 3.5 did not help. Neither did a fresh install of Ubuntu 12.04 from the live cd.
So the last thing I'm trying now is to install Ubuntu 12.10 fresh in place of 12.04, and hope that this can solve the problem. I've done this, but now it won't boot up at all. I've looked at the message boards and tried boot-repair, twice now, which did not work for me. [http://paste.ubuntu.com/5668730](http://paste.ubuntu.com/5668730)
I first selected /boot (/dev/sdb1) for installation of grub, and then /home (/dev/sda). I have also tried booting from grub-rescue prompt as described [http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash](http://askubuntu.com/questions/197833/recovering-from-grub-rescue-crash) but I can't get past the "ls" stage: every command I type returns either "error: bad filename" or "error: file not found".
I have an intel core i7 with 24G ram and an Nvidia GT200 GeForce GTX260 gfx card. If upgrading doesn't work the next step I am contemplating is to replace the graphics card, although I don't have any strong basis to believe that this is the problem.
Thanks for any help you can provide.

---

### Post by hazmat74 on 2013-04-01
This thread is a duplicate. Sorry, but I can't figure out how to remove it.

---

### Post by oldfred on 2013-04-01
Closed see
[http://ubuntuforums.org/showthread.php?t=2131428](http://ubuntuforums.org/showthread.php?t=2131428)

---

