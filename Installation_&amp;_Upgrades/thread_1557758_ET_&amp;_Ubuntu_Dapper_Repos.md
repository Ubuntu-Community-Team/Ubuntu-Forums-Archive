---
title: "ET &amp; Ubuntu Dapper Repos"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by hans796 on 2010-08-21
Installed Ubuntu Dapper 6.06 on a secondary PC just to have the opportunity to play Enemy Territory without problems.

All went well without bigger problems. Punkbuster could be upgraded via downloading punkbuster files instead of using pbsetup that didn't work on dapper.

After that I wanted to have 6.06 to do as much as possible.

Searched internet for working respos and here are my sources.list (if anyone needs it):

##deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://ftp.netspace.net.au/pub/ubuntu](http://ftp.netspace.net.au/pub/ubuntu) dapper-backports main restricted
deb [http://ftp.netspace.net.au/pub/ubuntu](http://ftp.netspace.net.au/pub/ubuntu) dapper-proposed main restricted
deb [http://ubuntu.indika.net.id](http://ubuntu.indika.net.id) dapper main restricted universe multiverse
deb [http://ubuntu.indika.net.id](http://ubuntu.indika.net.id) dapper-updates main restricted universe multiverse
deb [http://ubuntu.indika.net.id](http://ubuntu.indika.net.id) dapper-security main restricted universe multiverse

Change the .se in the first two lines, to where you live, .se = sweden

=D>

---

### Post by mörgæs on 2010-08-21
Thanks, but are you aware that 6.06 is unsupported (the desktop edition) and thus a security risk?

---

