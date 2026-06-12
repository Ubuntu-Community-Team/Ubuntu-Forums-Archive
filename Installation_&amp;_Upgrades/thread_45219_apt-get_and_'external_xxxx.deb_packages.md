---
title: "apt-get and 'external xxxx.deb packages"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by b.r.leeflang on 2005-06-29
Dear All,

I am comming from RedHat/Fedora installations. So I am currently figuring out how to install software on ubuntu (/debian) systems. This goes with 'apt-get'. I know 'sources' can be defined and by defining preferences I can  control which source gets preference for all or specified packages.  So far so good....

The thing I can not yet figure out is how to get a certain package installed that I downloaded from any source. So on my local machine I have a 'package-version.deb'  file.

HOW do I get apt-get to only work on this single file that I have ready to install......

I was always told good stories about apt-get.... So something trivial as asked for here must be possible.

Any comment is welcome

---

### Post by SQFreak on 2005-06-29
[QUOTE=b.r.leeflang]The thing I can not yet figure out is how to get a certain package installed that I downloaded from any source. So on my local machine I have a 'package-version.deb'  file.

HOW do I get apt-get to only work on this single file that I have ready to install......[/QUOTE]

```
sudo dpkg -i package-version.deb
``` should do it.

---

