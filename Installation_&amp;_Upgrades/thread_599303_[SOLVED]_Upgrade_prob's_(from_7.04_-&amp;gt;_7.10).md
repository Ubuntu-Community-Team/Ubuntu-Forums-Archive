---
title: "[SOLVED] Upgrade prob's (from 7.04 -&amp;gt; 7.10)"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by pcolamar on 2007-11-01
I am having problem upgrading (via update manager) from 7.04 to 7.10.

The process hangs on "Fetching the upgrades" and when I try to cancel, a windows opens with the following errors.

Any suggestion  ??
Thanks

Palmer

---------------------------- 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_AU.bz2) 

--------------

---

### Post by PmDematagoda on 2007-11-01
Try changing your server in System>Administration>Software Sources to another mirror and see if that solves your problem.

---

### Post by hoges on 2007-11-01
Failing that, download the alternative cd iso. Apparently you can upgrade through that.

---

### Post by pcolamar on 2007-11-01
> **PmDematagoda said:**
> Try changing your server in System>Administration>Software Sources to another mirror and see if that solves your problem.

Yes !!!

It did it.

It's finally downloading.

I will see in 40 min. if it's all ok ,( although I will download later the alternate CD as Hoges suggested,  just in case !)

thanks

---

