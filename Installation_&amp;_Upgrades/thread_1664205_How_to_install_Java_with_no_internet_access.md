---
title: "How to install Java with no internet access?"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by gino on 2011-01-10
Hi,
I need to install Java support (probably upgrade) on a Ubuntu 8.04 64 bit machine that does not have internet access. I do have access to a nearby windows machine with internet access.

Background: My company in its infinite wisdom decided to have a NAC authentication of some sort. After many emails they tell me now I am authorized to access the net (before the NAC thing it was working fine). When I try to log in I cant but if I try to go to the NAC website that will allow me presumably to log in it seems to try to but complains that I may have to install (or upgrade java). Of course I can not have internet access without accessing the NAC web site and I can not access it till I have java that I can not get since I have no internet access...etc., etc. 
I checked and I seem to have a version of java
$ java -version
java version "1.5.0"
so I assume I need to upgrade

Any help would be greatly appreciated. 

Cheers and many thanks in advance

Gino

---

### Post by davidmohammed on 2011-01-10
suggest use keryx - you'll need to use this [guide]("http://keryxproject.org/wiki/index.php?title=Running_Keryx_from_source") to install keryx for 8.04.  Then goto the keryx website for the tutorial how to use.

---

