---
title: "just sharing my upgrade issues"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by mcewen98 on 2005-10-14
I just wanted to share the experiences with upgrading to breezy from hoary.

I changed the sources.list hoary references to be breezy.  I then did apt-get update and apt-get dist-upgrade

I was prompted a few times about overwriting previous config files which I said not to all.

After everything was done and I rebooted, mythtv was gone, as was my ability to open up a remote desktop session with a vnc client.  The IVTV drivers for the tuner was also gone.. which I guess should not be a surprise since a the kernel was installed.

I think I might upgrade to the 686 kernel, then I"ll have to go through the setup of mythtv and ivtv again, which after doing it once I don't think will be too difficult.  

Everything else seems to work good though... apache, mysql, php, etc. are all working right.

Anybody else have these similar issues?

---

### Post by thewbman on 2005-10-15
I also upgraded to Breezy and lost mythtv.  Apache2, php and mysql all seem to be working fine by themselves.  When I try to run mythbackend is get the errors:

QSqlDatabase: QMYSQL3 driver not loaded
QSqlDatabase: available drivers:
2005-10-15 13:04:36.729 New DB connection, total: 1
2005-10-15 13:04:36.729 Unable to connect to databse!
2005-10-15 13:04:36.729 No error type from QSqlError? Strange...
2005-10-15 13:04:36.730 Failed to init MythConetext, exiting.

I'd really rather not reinstall mythtv and tweak it out.  I'm using mythtv 0.18, compiled from source.  Does anybody have an idea to fix this or should I just assume it's completely dead.  I haven't tried installing mythtv from packages, but that might be preferable to recompiling.

---

### Post by mcewen98 on 2005-10-15
I think I would assume it's completely dead and just set it up again.  Although, I seem to have an issue with that as well, but I haven't really gone back and looked at the directions either.  I had originally set up mythtv using apt-get.  I noticed the version with breezy is 0.18 rather than 0.17.

I think I may end up redoign my machine anyway.  It shouldn't be too much trouble if I just copy the configuration files for samba, vsftpd, apache, etc...and it will give me an excuse to buy some new hardware.

I'm somewhat dissapointed by the apt-get dist-upgrade...  I get an error at the login window about an invalid configuration too.  So who knows... if I reformat and install a fresh copy of breezy, it will be interesting to see how well, or how dissapointingly the dist-upgrade works for next time.

---

### Post by thewbman on 2005-10-15
Thanks for the reply.

I think that I will just end up starting mythtv agian from scratch.  I hate to loose all my configuration and tweaks, but that might be easier than trying to dig and see what went wrong.

btw, what site are you using to get your mythtv package?

---

### Post by mcewen98 on 2005-10-15
It comes from the breezy multiverse... which I believe is this line from the sources.list file:


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

---

### Post by steevc on 2005-10-16
My upgrade was also less than smooth. The actual downloading was fine and I answered the questions about changed file as best I could. The result was a system that just started up with a console rather than my nice KDE.

There seemed to be lots of locale errors.

After much Googling on another PC (Window) I tried

apt-get -f install

That fixed the locale issue, but still no GUI. startx was complaining about fonts and the path seemed to be wrong. Fixed that with

ap-get install xfonts-base

That actually got me into Gnome via startx. The next time I rebooted it went straight into KDE.

I still seem to have some issues with broken packages reported by the update manager. I'll try running some more updates to see if they go away.

Overall it's been a frustrating experience. Without access to another PC and Google I would have been totally stuck. I guess I could have booted from an old live CD, but it would have been a slow process to find possible solutions and try them out.

At least I have a system that looks to be mostly working. kmail seems to have a problem sending to some people, but that may be the problem with GPG that I've seen mentioned.

---

### Post by linuxgrrl on 2006-01-31
[QUOTE=thewbman]I also upgraded to Breezy and lost mythtv.  Apache2, php and mysql all seem to be working fine by themselves.  When I try to run mythbackend is get the errors:

QSqlDatabase: QMYSQL3 driver not loaded
QSqlDatabase: available drivers:
2005-10-15 13:04:36.729 New DB connection, total: 1
2005-10-15 13:04:36.729 Unable to connect to databse!
2005-10-15 13:04:36.729 No error type from QSqlError? Strange...
2005-10-15 13:04:36.730 Failed to init MythConetext, exiting.

I'd really rather not reinstall mythtv and tweak it out.  I'm using mythtv 0.18, compiled from source.  Does anybody have an idea to fix this or should I just assume it's completely dead.  I haven't tried installing mythtv from packages, but that might be preferable to recompiling.[/QUOTE]


try:
sudo apt-get install libqt3-mt-mysql
that fixed it for me

---

