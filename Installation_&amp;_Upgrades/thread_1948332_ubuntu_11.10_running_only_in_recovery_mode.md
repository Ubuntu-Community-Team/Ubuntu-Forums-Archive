---
title: "ubuntu 11.10 running only in recovery mode"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by lazy adventurer on 2012-03-28
Recently I revived my desktop and installed Ubuntu 11.10 with GNOME3 on it (I did not install debian due to its poor integration with compiz). After only one day of running, my machine reboots whenever I log into Ubuntu normally. The only way to work is to boot into the recovery mode and then proceed with normal boot up. This causes my display to come at a lower resolution and turns off compiz. I am scratching my head endlessly and trying to discover some error from the /var/log/*.log files and ~/.xsession-errors . Any pointers how to get normal mode running?

---

### Post by raja.genupula on 2012-03-28
is your system got all updates installed ? if not install all updates and then try again .

---

### Post by lazy adventurer on 2012-03-28
I installed all the updates but the problem remains.

---

### Post by lazy adventurer on 2012-03-30
Here are some of my findings:
1. System works perfectly fine in recovery mode
2. Works fine in console mode (through ctrl|alt+f1 etc.) even after normal boot
3. Issue is seen in live USB session as well

The major difference in recovery mode is that the monitor is not detected, and 1024x768 resolution is used, whereas my monitor has a 1600x900 display capability. The system reboots after using X in 1600x900 resolution. I am trying to check with older ubuntu and/or mint to see if the issue is there as well.

Any pointers to help me investigate the issue are highly appreciated.

---

### Post by lazy adventurer on 2012-04-11
It seems the issue is in the intel graphics driver. I saw that I successfully get full 1600x900 resolution with debian lenny, but not with debian squeeze. Any idea how to use an older version of the graphics driver in a newer ubuntu/debian?

---

### Post by samutopia on 2012-06-25
> **lazy adventurer said:**
> It seems the issue is in the intel graphics driver. I saw that I successfully get full 1600x900 resolution with debian lenny, but not with debian squeeze. Any idea how to use an older version of the graphics driver in a newer ubuntu/debian?

I had the same problem (could login through recovery mode, but not through regular mode) trying to set up ubuntu server on my old dell dimension e310. Finally I figured (with this mail) that the video was coming from an NVIDIA card I'd installed. Once I switched the VGA cable to the original motherboard port and rebooted, things started working well again.

---

