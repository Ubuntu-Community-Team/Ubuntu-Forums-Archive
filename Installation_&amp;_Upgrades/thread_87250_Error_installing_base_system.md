---
title: "Error installing base system"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by Wim on 2005-11-07
Hi,

I do get an error message when ubuntu is istalling the base system. (at about 74%).  It suggests to look at /target/var/log/bootstrap.log but I do not know how to get there.
I 'am a new and not experienced user and did erased my hard disk for partitioning (6G) and use an 166MMX PC

Anyone that can help?

Wim

---

### Post by carlosatbcn on 2005-11-07
I had the same problem.
After some tryings I let ubuntu to make the default partitions, and this error disappear, but I found more errors later, like no X installed.

Just now I'm trying again. It seems that now is going ok.
The problem is that after the first rebbot during the installation, ubuntu needs the CD , but is not asking for it!! 
After the first reboot, insert the CD, but not let the system boot from it. Ubuntu will continue the installation.
I cross my fingers.

regards

---

### Post by izm81 on 2005-11-08
I also had a problem installing Breezy... the process would stop, complaining that it couldn't read something (stopped at various points).  It ended up being a hardware incompatbility with my DVD drive (BENQ DW1640).  After enabling DMA, everything worked fine.

See Bug #16901, if this sounds like it might be the case for you.

Also, take a look at the related development thread (now closed): [http://ubuntuforums.org/showthread.php?p=388455](http://ubuntuforums.org/showthread.php?p=388455)

---

