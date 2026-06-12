---
title: "Slow Boot, ppp driver trying to load?"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by rangerdave on 2008-11-08
I just upgraded from 8.04 to 8.10, and I noticed my laptop now takes about 2 minutes longer to boot up.  I'm a linux newb, but following the advice I have found thus far online, I ran dmesg and I see the following:

> [   19.101598] type=1505 audit(1226119479.352:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4246
[   19.101820] type=1505 audit(1226119479.352:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4246
[   19.260795] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.550471] NET: Registered protocol family 17
[   90.217558] PPP generic driver version 2.4.2
[   90.281670] NET: Registered protocol family 10
[   90.282204] lo: Disabled Privacy Extensions
[   90.282749] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   91.068490] ACPI: WMI: Mapper loaded
[   91.087809] ACPI: \_SB_.PCI0.FNC2.IDE1.ODD1: found ejectable bay


There are obviously a lot more things, but that one had the largest gap in timestamp.  I look in the package manager, and I have 2.4.4 installed, not this 2.4.2.  I can't find any mention to this anywhere in the package manager.  This might have been something I manually installed when trying to get my Sprint EVDO card working, i just don't remember.  Any ideas on how to get that thing out of there?  Thanks in advance!

Dave

---

### Post by rangerdave on 2008-11-25
Guess this got moved to the Installation & Upgrades, even though I don't think that is the sole place this thread could exist.  Can nobody tell me how to remove something from loading at startup for Ubuntu?

Thanks in advance.


Dave

---

### Post by rangerdave on 2008-12-04
I figured it out.  I followed the directions here:

[http://ubuntuforums.org/showthread.php?t=971581&highlight=intrepid+slow+boot](http://ubuntuforums.org/showthread.php?t=971581&highlight=intrepid+slow+boot)

---

