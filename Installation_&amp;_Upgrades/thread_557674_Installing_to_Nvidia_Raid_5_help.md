---
title: "Installing to Nvidia Raid 5 help"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by Akrovah on 2007-09-22
Hello, I am pretty much a complete noob to the Linux world. I am trying to install Ubuntu 7.04 onto an Nvidia raid 5 array, which I just found out today through this process is not a true Hardware RAID. I'm not feeling fuzzy about that.

Anyway, when I get to the partition section of the setup, I of course see the four separate drives instead of the one logical drive. I need to keep the FakeRAID as I am still dual booting to Windows (triple booting technically - XP and Vista already installed) and I have already carved out an unpartitioned section for Linux to take over and have it's way with.

I have tried following the instructions here in the FakeRaidHowTo guide, as well as instructions from a previous thread [http://ubuntuforums.org/showthread.php?t=464758]("http://ubuntuforums.org/showthread.php?t=464758")

I even took the advise at the bottom of the FakeRaidHowTo in the RAID 5 notes about updating dmraid. My dmraid version is currently showing as 1.0.0.rc14
and it shows a device-mapper version of 4.11.0

When I type in the sudo dmraid -ay command I just get this message
ERROR: device-mapper target type "raid45" not in kernel
Which to me suggests an update to the Kernal itself is needed, but how can I do that with a Live CD? how do I do it at all really?

---

### Post by Akrovah on 2007-09-23
Any ideas?

---

