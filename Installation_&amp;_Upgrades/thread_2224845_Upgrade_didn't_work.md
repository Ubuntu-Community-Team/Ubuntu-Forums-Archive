---
title: "Upgrade didn't work"
date: 2014-05-18
forum: Installation &amp; Upgrades
---

### Post by BenTurpin on 2014-05-18
Ubuntu asked me if I wanted to upgrade to the new 14.04 and I pressed ok. After the download and installation, the computer needed to restart and now I have a black screen with lots of things telliung me I can push help for more info, only getting a list of command I can use, but I haven't got a clue what to do. So now I am unable to access my files in the ubuntu side, I also have window 7. I have seen threads with similar problems and looked at the suggestions, and to be honest I get lost in the yargon and still haven't got a clue. Should i reinstal from my window boot? Should I go back to ubuntu 13?
any advice would be welcome.
ton

---

### Post by Bashing-om on 2014-05-18
BenTurpin; Hello;

Let us "suppose" that you had a proprietary graphics driver in use in 13.10, and in the process of release upgrading to 14.04 the driver got broke.
Try the "nomodeset" boot option and see if you boot to a degraded GUI desk top.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) ##<- How to set NOMODESET and other kernel boot options in grub2

If that is a success, we can work on removing the broke graphics driver, and (RE-)installing a driver.

[INDENT]where there are solutions
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT]

---

