---
title: "Dual Boot deletion"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by mmr160 on 2007-06-15
On a Gateway ATX computer Windows XP Pro SP2 is loaded on main hard disk. Second hard disk is loaded with ubuntu v. 6.1o Edgy Eft. An automatic dual boot screen offers 4 choices on Start Up with ubuntu favored in an 8 second timeout.
    It is important to remove this Start Up dual boot choice since others using the same computer know nothing about Linux distributions or ubuntu. The screen choices unnecessarily complicate the boot process.
    Can someone tell me how to delete this Start Up routine and simply revert to opening Win XP Pro SP2 as before loading ubuntu. As Administrator I will still be able to use ubuntu when I choose, but I don't want others messing around with it.
    Thanks for your attention and comments.

---

### Post by confused57 on 2007-06-15
> **mmr160 said:**
> On a Gateway ATX computer Windows XP Pro SP2 is loaded on main hard disk. Second hard disk is loaded with ubuntu v. 6.1o Edgy Eft. An automatic dual boot screen offers 4 choices on Start Up with ubuntu favored in an 8 second timeout.
    It is important to remove this Start Up dual boot choice since others using the same computer know nothing about Linux distributions or ubuntu. The screen choices unnecessarily complicate the boot process.
    Can someone tell me how to delete this Start Up routine and simply revert to opening Win XP Pro SP2 as before loading ubuntu. As Administrator I will still be able to use ubuntu when I choose, but I don't want others messing around with it.
    Thanks for your attention and comments.
See this guide for editing your menu.lst & where to place your Window's entry:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Basically, you could copy & paste your Window's entry to just above the line  ###BEGIN AUTOMAGIC KERNELS LIST...Windows will boot by default, if default is set to 0.

You can hide the menu by removing the # in front of hiddenmenu, then you would need to press "Esc" to enter the grub boot menu at startup...you could also reduce the timeout to something like 3 seconds(no less than).

---

