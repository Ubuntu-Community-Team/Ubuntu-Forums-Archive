---
title: "install packages with no internet possible?"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by kleskjr on 2010-03-27
Hi ubuntu forum,
I have a general question: can I install packages in my Ubuntu, just using the live-CD but no network connection?

I broke my Ubuntu(9.10) and now can not log in, so I want to reinstall gnome, unfortunately I could not connect to internet, so I wonder if there is a way to use the live-CD as a source for the new software.

I would be really happy if I don't have to preinstall the whole system.

cheers

---

### Post by l.billon on 2010-03-27
Hi!
Try to uncomment the CDROM line in the /etc/apt/sources.list file.
Then do the update and upgrade

---

### Post by kleskjr on 2010-03-27
thanks!
i will reboot and try it immediately..

---

### Post by kleskjr on 2010-03-28
it didn't work 
i tried also with apt-cdrom but somehow it did not find the packages. I solved it manually downloading ubuntu-desktop.deb and gnome-sessions.deb. Now my Ubuntu is back!!!hura

---

### Post by richlyn9 on 2010-03-28
check this
[http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/](http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/)

---

