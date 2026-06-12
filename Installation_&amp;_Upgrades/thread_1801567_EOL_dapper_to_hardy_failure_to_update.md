---
title: "EOL dapper to hardy failure to update"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by techsoft3d on 2011-07-10
So I have a EOL dapper needed to get to hardy.

here is the source list,

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse

# Optional
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 

then apt-get update

followed by do-release-upgrade

that fails as the script puts this in sources.list.d/prerequists-sources.dapper.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main/debian-installer

thoughts?

---

### Post by dabl on 2011-07-10
> **techsoft3d said:**
>  I have a EOL dapper needed to get to hardy.


Why?  You have a 2006 version, which you were happily running yesterday. If you were happy in July 2011 with a 2006 operating system, what difference does it make whether or not you can update to a 2008 version?  Just stay with Dapper.






(or, you could install a 2010 or 2011 operating system ........)

---

### Post by mörgæs on 2011-07-10
Hi, welcome to the fora.

Both versions are obsolete:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

This means that no security bug fixes have been released for a long time.


Best is to try one of the supported versions in a live boot and after that a fresh install.

---

