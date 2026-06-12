---
title: "2 disks, 2 RAID arrays"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by mbsaerens on 2008-10-12
Hello

At this moment I have 2 HDDs of 320GB on an Gigabyte GA-P35C-DS3R mainboard (ICH9R).  The first 50 GiB of each disk are in an RAID0 array, giving me a 100GiB Partition holding my Vista installation, the rest of the diskspace is configured to be in an RAID1 array, containing my personal data.
Now I would like to switch from Vista to Ubuntu 8.04, but with the same setup.  I've been searching the net and found fakeRaid, dmraid and iswraid, but all guides are for just 1 array.  Running Ubuntu live and trying to use dmraid, gParted still shows my 2 HDDs seperatly (with mixed up partitions, but I don't mind since they'll disapear once I install Ubuntu) but fails to see the RAID configurations.

Has someone succeeded in installing Ubuntu the way I would like to do it?

Great thanks in advance!

---

### Post by chongzv08 on 2008-10-12
BFV **[gate Valve](http://www.valvesupplier.net/)** also possess the test lab with various of examination equipment for material chemical composition analysis, physical property and non-destructive examinat-ions such as RT,UT,MT,PT . the website:[www.valvesupplier.net](http://www.valvesupplier.net)

---

### Post by mbsaerens on 2008-10-14
*bump*
Nobody?!  Hard to believe I'm the first one to do this.
Any help is appreciated :)

---

### Post by streamsanddragonflies on 2008-10-17
I am still very new to linux and raid!  I my self am preparing to use 2 partitions in a raid0 array as you have. I read this software RAID HOW-TO and it helped immensely:

[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Furthurmore, in
[https://help.ubuntu.com/8.04/installation-guide/i386/module-details.html](https://help.ubuntu.com/8.04/installation-guide/i386/module-details.html)

towards bottom of page- look at **manual install** (you need the **alternate install cd**) to select your Ubuntu software raid partitions/disks.

I don't know anything about dmraid and just glanced at fakeRaid so sorry I can't help you there, but if you choose to go with ubuntu's software raid (included in the kernel) you can select raid0!  

[I]"To create a MD device, you need to have the desired partitions it should consist of marked for use in a RAID. (This is done in partman in the Partition settings menu where you should select Use as: &#8594; physical volume for RAID.)
[Warning] 	

Support for MD is a relatively new addition to the installer. You may experience problems for some RAID levels and in combination with some bootloaders if you try to use MD for the root (/) filesystem. For experienced users, it may be possible to work around some of these problems by executing some configuration or installation steps manually from a shell.

Next, you should choose Configure software RAID from the main partman menu. (The menu will only appear after you mark at least one partition for use as physical volume for RAID.) On the first screen of mdcfg simply select Create MD device. You will be presented with a list of supported types of MD devices, from which you should choose one (e.g. RAID1). What follows depends on the type of MD you selected.

RAID0 is simple &#8212; you will be issued with the list of available RAID partitions and your only task is to select the partitions which will form the MD..."  [/I]

Hope that this is helpful.

---

### Post by craigcrawford114 on 2008-10-17
Hi mbsaerens,

I am also trying to install Ubuntu on a RAID array. I have a RocketRAID 2320 in a RAID 5 array and Ubuntu does not detect any devices.

Completely and utterly lost on this one.

Any help for me and mbsaerens is much appreciated :)

---

