---
title: "Can a monitor hang Ubuntu?"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Roinou on 2011-04-29
Hi all,

I've been using Ubuntu for quite a while, and I'm wandering about something.

I remember having quite some problems installing 10.04, where as the live CD was hanging. After some search on the forums, I realized the NVidia drivers where hanging the whole system. It is happening again with 11.04, and I don't know why. There is nothing exotic with my conf, I have a standard NVidia Winfast card, PCI express with a normal mother board. Now that I'm thinking, my monitor is a REALLY old flat screen resolution no better than 800*600. Could that be a reason everything is hanging? I have no other monitor to test, so I'm wandering if the screen could create a problem with the NVidia driver, and hang Ubuntu.

Thanks for your help folks.

---

### Post by dabl on 2011-04-29
Yes, it can.  I think the Nvidia driver is looking for EDID response and not getting it, or else it is getting an EDID value that appears to be erroneous.  You may need to manually insert a modeline in your /etc/X11/xorg.conf file to set the monitor mode.

Take a look at the log file at /var/log/Xorg.0.log, and look for error messages there.

Here's a case of troubleshooting that type of problem -- maybe it will help:  [http://kubuntuforums.net/forums/index.php?topic=3114181.msg245873#msg245873](http://kubuntuforums.net/forums/index.php?topic=3114181.msg245873#msg245873)

---

