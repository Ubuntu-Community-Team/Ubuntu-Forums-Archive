---
title: "Having or Had a Purple or Black Screen Problem?  See Here."
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2011-05-11
If you had or have a black screen or purple screen problem in Natty, please be counted, add support by subscribing to this Launch Pad Bug:[B][SIZE=2]
Xorg's HAL causes Purple Screen or Black Screen on GDM startup.[/SIZE][/B]
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/781445](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/781445)

Through helping people with these problems in the Ubuntu Support Forum (Installations and Upgrades) and through this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
...this bug (above) seems to be where this problem is originating.  It affects this problem with all video hardware types.

As I said in this bug report:
"Normal users should not have to be highly skilled "techies" to manually  bypass a broken part of a system to make a released distribution work  during an install or distribution upgrade"

---

### Post by MAFoElffen on 2011-05-13
> **MAFoElffen said:**
> If you had or have a black screen or purple screen problem in Natty, please be counted, add support by subscribing to this Launch Pad Bug:[B][SIZE=2]
Xorg's HAL causes Purple Screen or Black Screen on GDM startup.[/SIZE][/B]
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/781445](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/781445)

Through helping people with these problems in the Ubuntu Support Forum (Installations and Upgrades) and through this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
...this bug (above) seems to be where this problem is originating.  It affects this problem with all video hardware types.

As I said in this bug report:
"Normal users should not have to be highly skilled "techies" to manually  bypass a broken part of a system to make a released distribution work  during an install or distribution upgrade"
(Bump)
I submitted this BUG Report on behalf of the support community, even though it personally does not affect me.  Although, if need be, I guess I could recreate it, so it does...  ***If others do not subscribe, it will die.*** 

What is HAL?  HAL is used to query hardware and return thee hardware's data for use with xorg.  Xrandr uses HAL to query monitors and it is used to construct the xorg.conf.

Translation- A utility is that is supposed to help a graphics session start in a visible mode is locking up that session instead. 

This bug is not specific to a type of video hardware chipset, as it seems to affect a lot of different manufacturers and types.

---

