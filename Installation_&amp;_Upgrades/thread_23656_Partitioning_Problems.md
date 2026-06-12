---
title: "Partitioning Problems"
date: 2005-04-03
forum: Installation &amp; Upgrades
---

### Post by GnuKemist on 2005-04-03
All,

Last night I decided to re-install Hoary onto my AMD64 desktop.  I downloaded the latest RC and proceeded to reboot.  Went through the first dialogs until I got stuck on the partitioning section.  I have tried different methods (most of the time I choose to erase the entire disk) but always with the same outcome:  Input/Output error during read on /dev/ide/host0/bus0/target0/lun0/disc.  Am not sure whether this refers to my DVD-ROM, the actual CD I'm using or worse, if it is my HD itself.  I have tired installing other versions of Ubuntu, all with the same result.  I finally tried Libranet and it worked w/o a glitch.  Can someone shed some light?

Thanks in advance,

---

### Post by GnuKemist on 2005-04-04
Just thought I'd post the solution to my problem in case someone else has the same issue.  The following command seem to have "fixed" it:

hdparm -d 1 -A 1 -m 16 -u 1 -a 64 /dev/hda

---

