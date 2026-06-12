---
title: "Update Manager Aborted Upgrade"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by smflorkey on 2010-12-31
Ubuntu Studio (no idea what version, no idea how to find out) Update Manager has been saying 10.04 is ready for quite some time, but I cannot install the upgrade.

The first time, more than a month ago, it had problems with Java and aborted.

This time it couldn't find a repository in NZ so it threw up its (virtual) hands and gave up.

Should I even try to upgrade?  I keep installing maintenance and security updates (except Adobe Flash Player which Adobe cannot identify).  It does most of what I want it to do.  Does 10.04 (or 10.10) really matter?

Assuming I try for US 10.04 LTS again, how do I get it past its problems?

Thanks, 
Steve

---

### Post by tommcd on 2011-01-01
> **smflorkey said:**
> Ubuntu Studio (no idea what version, no idea how to find out) Update Manager has been saying 10.04 is ready for quite some time, but I cannot install the upgrade.
This likely means that you are using either Ubuntu 8.04 or 9.10. To find out which version you are using, open a terminal and use:
```
cat /etc/lsb-release
```
> **smflorkey said:**
> 
The first time, more than a month ago, it had problems with Java and aborted.
The best way to upgrade Ubuntu and have a trouble free experience is to do a clean install. I never do dist-upgrades; and I never have problems with Ubuntu. Since you have been having problems trying to dist-upgrade Ubuntu, there is a high probability that it may not go well.
> **smflorkey said:**
> 
This time it couldn't find a repository in NZ so it threw up its (virtual) hands and gave up.
Since your profile says you are in California, why are you using a mirror in New Zealand (NZ)??
> **smflorkey said:**
> 
Should I even try to upgrade?  I keep installing maintenance and security updates (except Adobe Flash Player which Adobe cannot identify).  It does most of what I want it to do.  Does 10.04 (or 10.10) really matter?

Both Ubuntu 8.04 and 9.10 will reach end of life in April 2011; although 8.04 will still have updates until 2013 for the server edition. So you will need to upgrade by April 2011:
[http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html](http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html)
Also, and especially since you are using Ubuntu Studio, the newest version of ubuntu studio (10.10) will have newer versions of all the multimedia apps you use.
It is your choice though.

---

