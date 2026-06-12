---
title: "fax software ?"
date: 2004-11-03
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2004-11-03
Has anyone had good success setting up and using a particular fax program on Ubuntu?  If so could you let me know, I have no idea where to start.  It will be on a notebook with a winmodem which also poses some challenges.

Thanks for any suggestions.

Jim

---

### Post by az on 2004-11-03
I like efax-gtk.  I think it is in universe.

Many winmodems have linux support.  What kind is it?

---

### Post by jamaas on 2004-11-03
Thanks azz,

I tried to load efax-gtk using the synaptic package manager but got some error.   In my ignorance, what is "universe"?

My winmodem is in a HP ze5200 notebook pc and is apparently a ALi Corp M5457 AC'97 Modem Controller, if that makes any sense.  Suggestions?

Thanks a bunch

Jim


[QUOTE=azz]I like efax-gtk.  I think it is in universe.

Many winmodems have linux support.  What kind is it?[/QUOTE]

---

### Post by az on 2004-11-03
Get this:
[http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

You may need either the slmodem packages, the pctel source ot eh drivwers from linuxant.

I do not know if the slmodem stuff is on the cd:

[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/)

Either way, you will need to install your linux-headers and compile the drivers for your modem.  It is not too hard.  Tell me what the output of scanmodem (see above - save it to a floppy) is...



Universe is another repository of packages.  Essentially all the debian sid packages that compile with a warty base system.  You need to add it to your repositories in synaptic.  There is a faq aboutthis, but it is only a few clicks away.  You already have it in the default /etc/apt/sources.list but need to activate it (uncomment - if you are doing it by hand...)

Obviously, if you cannot get onto the net, never mind...

---

