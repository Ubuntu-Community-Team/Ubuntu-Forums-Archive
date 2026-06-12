---
title: "How to install unstable munin"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by BarsMonster2 on 2009-12-17
Hi there, I am on Ubuntu Server 9.10

I really need to upgrade munin from 1.2.6-13 to anything newer, cause I am facing an issue in 1.2.6-13 which is fixed in 1.2.6-14. Preferably I would even go for 1.4.

Could someone tell me how to upgrade? I tried to install it from sources, but it is definitely not created for Ubuntu, it installs to /opt/munin, so I would have to potentially alot of changes to relocate it to /usr/local/munin to match default Ubuntu configuration. 

How do I know if it is available as "unstable" and how to install unstable things?
tried apt-get -t unstable install munin and apt-get install munin/unstable - it sayd I already have latest version :-(

---

### Post by everythingsround on 2009-12-21
Giving the 1.4 source a go, found this post. If I get anywhere I'll post back.  
This may help your update issue:
[http://www.ubuntugeek.com/monitoring-servers-and-clients-using-munin-in-ubuntu.html](http://www.ubuntugeek.com/monitoring-servers-and-clients-using-munin-in-ubuntu.html)
Particularly in the conversion going on in the comments...
Bill says:
AUGUST 28, 2009 AT 4:19 PM
do this to properly force the update&#8230;

sudo /bin/sh
su - munin -s /bin/sh munin-update
exit

---

