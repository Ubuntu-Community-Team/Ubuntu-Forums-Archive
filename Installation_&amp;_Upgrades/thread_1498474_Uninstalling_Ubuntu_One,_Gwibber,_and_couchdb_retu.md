---
title: "Uninstalling Ubuntu One, Gwibber, and couchdb returned performance to Karmic levels"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by hreichgott on 2010-05-31
I had noticed that after upgrading to 10.04 everything on my computer ran much more slowly.... sometimes taking up to 1-2 full minutes to open a Firefox window, System Monitor, Gedit or even a terminal.

Not too much of a load on the CPUs, but memory usage was at 80%-90% of my 500 mb even with no applications running, just with the operating system.

Uninstalling Ubuntu One, Gwibber, and couchdb (sudo apt-get purge couchdb*) made everything much faster, and memory usage is now down to 35%-45%!  That's more like what I remember from Karmic.

I can still use Ubuntu One through its website.  No need for ubuntuone-syncdaemon to write to my hard drive every 3 seconds.

Caveat: Someone mentioned in this forum 
[http://ubuntuforums.org/showthread.php?t=1267900](http://ubuntuforums.org/showthread.php?t=1267900)
that removing couchdb can break Evolution, at least as of Sept 2009.  I don't use Evolution so I always uninstall it right away. If anyone knows of any other applications that can be broken by removing couchdb, please speak up.  thanks

Using Ubuntu Studio 10.04 on an IBM Lenovo Thinkpad T60 with 2 CPUs and 500 mb RAM

---

