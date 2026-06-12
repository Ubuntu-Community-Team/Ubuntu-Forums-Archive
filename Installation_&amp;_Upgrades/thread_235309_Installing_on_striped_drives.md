---
title: "Installing on striped drives"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by egd on 2006-08-12
Hi

I'm in the process of downloading ubuntu-6.06.1 desktop and intend replacing my existing xp installation entirely (if I need to access a win environment again I'll do that via VMWare).

The PC currently boots off a striped drive pair connected via SATA interface to a Promise RAID controller.  Is this likely to present me with problems on install?

Running Ubuntu ubuntu-6.06 from a livecd boot, all my NTFS HDDs (including the striped pair) are detected by ubuntu-6.06, but not accessible (ie I cannot browse them at all).  I'm not sure whether this is a hardware, liveboot session, or Ubuntu thing.  There would be little point installing Ubuntu only to find that my NTFS partitions are not even readable (the plan is to convert them all to ext3 in time).

thanks in advance from someone who REALLY wants to get off the MS bus.

---

### Post by egd on 2006-08-13
Ok, I've booted from ubuntu-6.06.1 desktop and confirm that Ubuntu is having difficulty recognising my Raid cotroller and also my SATAII controller, both from Promise Technology, Inc.

The RAID controller is a FastTrak S150 TX2plus
The SATAII controller is a SATA300 TX4

Whilst it sees all attached drives, it cannot access them.  Promise's website makes Redhat and SuSE drivers available.  Has anyone had any success using either of these drivers in Ubuntu?

Searching the forums I've found a post that indicates Dapper Drake supports the SATA300 TX4 out of the box [http://ubuntuforums.org/showthread.php?t=103808](http://ubuntuforums.org/showthread.php?t=103808).  Does running Drake in livecd mode preclude access to NTFS partitions?

---

### Post by egd on 2006-08-13
back on windows :(, what does a guy have to do to get help around here?

---

### Post by gerbman on 2006-08-16
> **egd said:**
> back on windows :(, what does a guy have to do to get help around here?People will help you if they know the answer. :) Any luck yet? I am going to buy a SATA RAID controller for level 1 RAID with two 250GB SATA drives. Anyone know if I'll be able to install to that setup?

---

### Post by silvagroup on 2006-08-17
you may want to check this post and do a search on sata and raid drive, there seems to be some major problems in this area, mine is a real horror story wiping out my system check - Default boot loader problem - post out before you try it:( and be very careful if you have ab=ny critical data.:-&

---

### Post by gerbman on 2006-08-17
> **silvagroup said:**
> you may want to check this post and do a search on sata and raid drive, there seems to be some major problems in this area, mine is a real horror story wiping out my system check - Default boot loader problem - post out before you try it:( and be very careful if you have ab=ny critical data.:-&Thanks. I decided to go with a Rosewill SATA RAID controller, chipset SIL3114 with 2x Maxtor 250GB drives. We'll see how it goes.

---

### Post by egd on 2006-08-18
> **gerbman said:**
> I am going to buy a SATA RAID controller for level 1 RAID with two 250GB SATA drives. Anyone know if I'll be able to install to that setup?

My guess is that if the raid card is not hardware raid then the answer is no insofar as you will be unlikely to boot from it, but may be able to access the raid partition(s) after booting off another hdd.

---

