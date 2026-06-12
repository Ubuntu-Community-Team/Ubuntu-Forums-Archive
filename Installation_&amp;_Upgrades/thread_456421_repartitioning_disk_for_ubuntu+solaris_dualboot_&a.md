---
title: "repartitioning disk for ubuntu+solaris dualboot &amp; preserving the data?"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by Heliix on 2007-05-27
Hello,
I'd like to install Solaris next to Ubuntu, as I want/need to learn Solaris. The problem is my current partition layout isn't very wise:

Disk /dev/sda: 100.0 GB
( Mounted on ) Device...........Size...Part. type....System
( /boot )........../dev/sda1.......30M...83...........Linux
( *swap* )......./dev/sda2.........2G...82...........Linux swap / Solaris
( / )................./dev/sda3.........6G...83............Linux
/dev/sda4                                                        Extended
( /home )........../dev/sda5........ 9.7G...83............Linux
( /mnt/data )...../dev/sda6..........20G...83............Linux
( /mnt/share ).../dev/sda7..........49G...83............Linux
( /var )............../dev/sda8..........7.1...83.............Linux


I'd like to create something like

( Mounted on ) Device..............Size...Part. type...System
( /boot )........../dev/sda1.........30M...83.............Linux
( solaris )......../dev/sda2.........10G...82.............Linux swap / Solaris
( / )................./dev/sda3.........10G...83.............Linux
/dev/sda4                                                        Extended
( /home )........../dev/sda5........9.7G...83............Linux
( *swap* )........./dev/sda6..........2G....82...........Linux swap / Solaris
( /mnt/data )....../dev/sda7.......~65G...83...........Linux

I don't need separate /var and I don't necessarily need my data to be accessible from Solaris, though it would be better. I think this layout should be fine but I'm open to any suggestions regarding this point.

The question is: is it possible to repartition the harddisk without having to reinstall Ubuntu? I guess not because all three primary partitions are already taken and are too small to be helpful. I'd like to preserve my programs and configuration-is it possible to backup the complete system (/boot, /etc, /usr..) and then renew it from the backup? I have too many specific programmes I don't want to loose.
Thanks in advance.

---

