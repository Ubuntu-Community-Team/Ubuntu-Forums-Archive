---
title: "possible to install 4 operating systems?"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by fuzzylogic25 on 2010-08-11
To put it briefly, I want to install the following 4 operating systems on my laptop:
(will write underneith for why I want each)

1. Windows XP
- comes in handy for several things from time to time, especially when in rare occassions i lend to someone who does not know what linux is. this will stay on laptop forever
2. Ubuntu
- what i want to use now whenever i need to do some work
3. Debian
- for testing purposes, to see if this linux is right for me
4. Slackware
- for testing purposes, to see if this linux is right for me. i hear this one is best linux to use if u want to learn unix as well.

I do have a computer where I do all my work on, running windows xp unfortunately. But it has come to a point where reliability and security is far too important for me so I want to make the switch to linux. I dont want another OS which does everything for u, so in long term i think debian or slackware is best for me. I will have to decide once i have trialled them out.

so is this situation possible? also, in terms of partitions...i know u can have only one logical partition, would that cause a problem?

---

### Post by oldfred on 2010-08-11
You can have many system installs if you have enough space. I have 3 drives 4 installs and space for several others. My 3 main installs are my last Ubuntu, my current Ubuntu 10.04 and my next Ubuntu 10.10. Each is in a 20-25GB / (root) partition with all my data in separate partitions but mounted into each so whatever I boot I have all the same files & firefox bookmarks. I do not recommend sharing /home as some settings may conflict. If you are just upgrading then using the same /home makes sense. But with a /data I do not have to worry about settings. I copy some settings from one /home if I think I might need them.

Partitioning basics with some info on /data older but still valid by bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by andrew.46 on 2010-08-27
Hi fuzzylogic25,

Have you considered running the 'extra' installations as Virtual Machines? The easiest way to do this would be with Virtualbox. On my own system I have run many, many operating systems in this way with no problems, just ensure that your computer has a decent amount of ram...

Andrew

---

### Post by M93 on 2010-08-27
yes virtualbox is a gr8 solution, i had a time when i was using ubuntu as the base and had win7, winXP, openSUSE all virtual
and didnt have problems except for 3GB ram :)

---

### Post by fuzzylogic25 on 2010-08-31
thank you, i shall try that out.

i am not sure what OS i will be using in the long term but i am pretty certain it wont be ubuntu. I will trialing/testing slackware, debian, some other linux variations, freebsd and probably also open solaris. so im hoping they can all run properly. i only have 1.86ghz core duo processer with 2.5gb ram. i guess i can get some more ram easily.

---

### Post by andrew.46 on 2010-08-31
Hi fuzzy,

> **fuzzylogic25 said:**
> i only have 1.86ghz core duo processer with 2.5gb ram. i guess i can get some more ram easily.

I have the same, a Dell Latitude D520 with 2 gig ram. This runs a Slackware host and guests of Windows 7 and Lucid Lynx with no trouble at all. I allocate 1 gig to each of the guests and only have one open at a time :).

Andrew

---

