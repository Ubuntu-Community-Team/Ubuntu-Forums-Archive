---
title: "Best way to upgrade production 10.04 server?"
date: 2016-11-20
forum: Installation &amp; Upgrades
---

### Post by melat0nin on 2016-11-20
Hello all

I have a client with a production website running on server 10.04 LTS. Needless to say, it needs to be upgraded. I'm wondering what the best option is -- attempt in-place upgrading, or wipe and start again with 14.04 LTS.

It's a fairly minimal setup -- LAMP and Webmin with the website running on /var/www (so default setup). It *should* be possible to just take a tarball of the site and its database, wipe the machine, and re-instate it, but since this is a production machine I'd rather avoid any potential mishaps (and downtime) that this might involve. Having said that, trying to upgrade such an old setup in-place might also cause lots of problems.

What would you do?

---

### Post by TheFu on 2016-11-20
I would make an image of the system, install it into a virtual machine and test the different upgrade methods at least 3 times each, taking careful notes along the way.  Lots and lots of things have changed since 2010 - major networking changes, major apache upgrades, and people use mariaDB these days instead of mysql.

I'd also just do a pure DB dump and file copy effort to start fresh on 16.04 without doing any program/OS migrations at all.

Didn't php change versions like 4 times over this period too? Planning to move to a new version of php?

Sounds like you know what the difficulties will be, it is just a matter of trying each to see which has the least impact.  It is also a good time to upgrade to newer HW and move to a VM.  VM's add so much flexibility that I'd never want to install something like this on physical HW again.

---

