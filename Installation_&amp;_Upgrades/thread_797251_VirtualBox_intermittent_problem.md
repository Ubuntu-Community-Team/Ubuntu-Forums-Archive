---
title: "VirtualBox intermittent problem"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by aaronp on 2008-05-17
Hi all,

I am having some issues with VirtualBox on my Ubuntu 8.04 (KDE desktop) machine.

Trying to install Windows XP in a virtual drive and it all goes well then all of a sudden it is as if the 'CPU' in the Virtual machine stops working for about 5 minutes at a time. Each 5 minute stint is broken up only by about 10 seconds of activity. (i.e. when Windows setup said it had 3 minutes to go it actually took about 45 minutes!!)
During the periods which it appears unresponsive the little green 'light' on the Virtual harddisk indicator is static. During the short periods of activity, this 'light' flashes between red and green quickly.

I deleted the entire virtual drive and created a new one but after the installation appeared to be going smoothly for a fair while it then started to grind to a halt again.

Anyone know of this problem?

thanks
Aaron

---

### Post by aaronp on 2008-05-18
All,
Further to my problem above, I tried VMWare Server and seem to be hitting similar issues. The installation runs smoothly until about 5 minutes to go and then starts periodically saying 'Operation on file "/media/vol1/WinXPVM/" failed (Input/output error)'

Then gives the option to abort, retry or continue (pass the error to the Guest)
Retry just gives me the same error, Continue seems to allow the setup to continue but the error returns within minutes. After hitting continue a few times I seem to be getting similar activity as my VirtualBox problem above.

I am stumped.

Any thoughts?
Thanks
Aaron

---

