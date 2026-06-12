---
title: "Do-release-upgrade 15.04-16.04 &quot;not supported by this tool?&quot;"
date: 2016-10-12
forum: Installation &amp; Upgrades
---

### Post by airplanesimen on 2016-10-12
Hello forums. 

I was just trying to upgrade to a LTS release on my vps. Turns out that I can't just use Do-release-upgrade and wait for it to install. 

It gave me following errors ;

```
 Reading cache

Checking package manager

Can not upgrade

An upgrade from 'vivid' to 'xenial' is not supported with this tool.
=== Command detached from window (Wed Oct 12 15:59:47 2016) ===
=== Command terminated with exit status 1 (Wed Oct 12 15:59:57 2016) ===
















[screen is terminating]
root@serverhost:~#
``` 

I'm not sure how to proceed, and I'm currently on a mobile device using ssh to remote control the vps. 

Thanks for any guidance :)

---

### Post by ubfan1 on 2016-10-12
You will probably have to upgrade your 15.04 to 15.10 before doing the 16.04 upgrade.  Since both 15.04 and 15.10 are obsolete, (set the source repositories to  things like: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) vivid main.
etc.   Probably far easier to backup your personal files, and do a fresh install of 16.04, using the "something else" and select the existing 15.05 partitions for the 16.04.

---

