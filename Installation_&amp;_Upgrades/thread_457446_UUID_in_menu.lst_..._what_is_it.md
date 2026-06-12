---
title: "UUID in menu.lst ... what is it?"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by mijj on 2007-05-28
the upgrade from 2.6.20-15 to 2.6.20-16 included a change in the UUID.

I could only get the sys to reboot into 2.6.20-16 by changing the UUID back to the old one used by 2.6.20-15.

what purpose does the UUID serve?

I've had enough of messing round with menu.lst for quite a while (being a novice, it was some time befor i thought of changing the UUID to get the updated sys to work)

so .. to same more wasted effort .. can i safely leave off the bit in the menu.lst where it specifies the UUID?

---

### Post by Jussi Kukkonen on 2007-05-28
I can't tell why yours broke, but the reason for using UUIDs is that device names may change without warning between reboots.

---

### Post by theonlykman on 2007-05-28
yeah, 16 and 15 werent working after the upgrade so I just changed both "root=" to /dev/sda3 (the parition on which I installed ubuntu) and they both work fine now. So Im confused, Is having the root field necessary?

---

### Post by mijj on 2007-05-28
oh .. i noticed my main drive has changed from sda to hda.

---

