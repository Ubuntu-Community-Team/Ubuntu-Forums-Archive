---
title: "pppoe disconnections"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cookiecruncher on 2010-03-06
I use pppoeconf to setup my DSL connection and dial in with 'pon dsl-provider'.

Recently I am being disconnected without reason.

After initially connecting, my '/etc/resolve.conf' file is correctly updated and my connection is displayed under 'ifconfig' as 'ppp0'.

When I am disconnected the 'resolve.conf' file changes to ```
# cat resolv.conf 
nameserver 192.168.0.1
nameserver 192.168.0.1
```At this point the ppp0 connection is still up, but the internet is inaccessible.

Anyone else having this problem?.  It seems to have started around about a week ago.

To access the internet I type 'poff -a' to disconnect and then 'pon dsl-provider' to connect.


EDIT:
This is happening when I boot up as well.

EDIT 2:
Edited out.

EDIT 3:
Problem is NOT caused by Akregator OR Knemo, as this problem has just occurred with both disabled.

EDIT4:
This problem seems to be caused by my DSL router.  If I manually assign myself an IP address, then this problem does not occur.

---

