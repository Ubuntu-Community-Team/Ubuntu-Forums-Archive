---
title: "Installation hangs at verifying the installation configuration"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by bratman91 on 2011-02-21
I am trying to install Ubuntu 10.10 on a Dell Latitude 1001 laptop which has XP installed. I have selected the option for Ubuntu to run alongside Windows but, on selecting the Ubuntu option at boot up, the installation stalls at "Verifying the Installation Configuration". Before this window came up, a very brief text message flashed on the screen - something like "getpwuid failed" (it was on the screen for only a second or less, so I didn't have chance to note it down.  Does anyone have any suggestions as to what may be wrong (I have never used Ubuntu so please make any suggestions very simple).

---

### Post by Quackers on 2011-02-21
How many primary partitions are currently in use on your system? 4 is the maximum on any hard drive. If you have 4 already the installer could be trying to stop you make a serious mistake.

---

### Post by bratman91 on 2011-02-21
> **Quackers said:**
> How many primary partitions are currently in use on your system? 4 is the maximum on any hard drive. If you have 4 already the installer could be trying to stop you make a serious mistake.
  I am not sure but the laptop is as purchased and has not been added to or tweaked in any way do I doubt that it already has 4 partitions.

---

### Post by sites on 2011-02-21
> **bratman91 said:**
> I am not sure but the laptop is as purchased and has not been added to or tweaked in any way do I doubt that it already has 4 partitions.

Just because you didn't alter the disk doesn't mean it wasn't shipped from the manufacturer without extra partitions.  Lots of computers are sold with extra partitions for recovery, maintenance, etc.  You should check the disk from a live environment for partitions & health status using Disk Utility.  It could even have bad sectors preventing installation.

---

### Post by bratman91 on 2011-02-21
> **sites said:**
> Just because you didn't alter the disk doesn't mean it wasn't shipped from the manufacturer without extra partitions.  Lots of computers are sold with extra partitions for recovery, maintenance, etc.  You should check the disk from a live environment for partitions & health status using Disk Utility.  It could even have bad sectors preventing installation.
  Ihave just had a look at the specs for this laptop and it has only 256Kb of RAM - I suspect that this is the problem. I think I have a spare memory card for this laptop so I'll add it and see what happens.

---

