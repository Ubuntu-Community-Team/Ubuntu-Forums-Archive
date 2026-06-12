---
title: "Corrupted GRUB after updating fresh install of 17.10"
date: 2018-03-13
forum: Installation &amp; Upgrades
---

### Post by serapis5 on 2018-03-13
I just did a completely fresh install of Ubuntu 17.10, restored all of my personal files and all is working well for the most part.  I dual boot with Windows 10 and the installation and reboots went smoothly.  Then I did the updates and now GRUB is corrupted.  It still works, but it is like I have 2 GRUB menus overlaying each other.  One is White on Purple Background and one is White on Black background.  as I scroll up and down the list, it changes back and forth between the two color schemes (I have attached a photo).  I tried un-installing GRUB and then reinstalling it, same results.  I tried installing a GRUB theme and got THREE menus overlaying.  So I removed GRUB theme.  Back to original issue.  I have looked for days for this issue on the forums.  If it is here already I apologize.  But any help you can provide is appreciated.

---

### Post by oldfred on 2018-03-13
May be a bug.

 Graphics menu issue flickering menu
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1752767](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1752767)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1748028](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1748028)

Several fixes in comments. May be fixed if you add proposed repository (which normally is not recommended).

---

### Post by serapis5 on 2018-03-14
Thank you oldfred.  Removing the --append tag solved the issue.  I appreciate the advice.

---

