---
title: "failure upgrading to 10.04 from 9.1"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by jtmedin on 2010-06-09
Have a dual boot: vista & ubuntu (64bit). Clicked the upgrade to 10.04 in update manager & spent a couple of hours downloading & installing. Had several requests about menu.lst. Which i replied keep the current Big mistake (i think) because on the reboot all the options are for 9.1. Tried the top option and 10.04? (i think) comes up but mouse & keyboard are inop. Booted with super grub cd & let it boot gnu/linux. Looks like 10.04 came up (how can u tell?) and seems to run ok. So what can i do to get the 10.04 options when rebooting without the grub cd? TIA

---

### Post by Peter09 on 2010-06-10
If you can get into recovery mode it might be worth updateing and upgrading.
 
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```
 
this will attempt to finalise your upgrade to Lucid, if you actually have done so.

---

