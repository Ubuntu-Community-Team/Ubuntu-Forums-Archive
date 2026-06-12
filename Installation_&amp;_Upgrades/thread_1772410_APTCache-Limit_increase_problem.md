---
title: "APT:Cache-Limit increase problem"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by scottholmes on 2011-05-31
I'm recently receiving error message:  E:Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf), E:Error occurred while processing libguile-ltdl-1 (NewFileVer1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

I have tried to increase the cache by adding the line

APT::Cache-Limit “10000000&#8243;;
to /etc/apt/apt.conf.d/70debconf but it has no effect.  This is on a Ubuntu Lucid 10.04 LTS

It is apparently getting the value from elsewhere.

Thanks, Scott

---

### Post by scottholmes on 2011-05-31
I don't have an explanation but I did remove the repository for chromium, the karmic entry, and was able to reestablish connection to my apt list.

---

