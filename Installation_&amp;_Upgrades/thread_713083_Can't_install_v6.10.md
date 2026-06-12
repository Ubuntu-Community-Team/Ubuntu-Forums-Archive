---
title: "Can't install v6.10"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by copan1122 on 2008-03-02
I can't get v6.10 to install. (This version came with "Ubuntu Linux for Dummies book.) The machine is  an Intel Pentium Dual-core. At "prepare disk space" there is only the option for manual edit partition table. I get a "no device found" message in Gparted. My guess is that because the harddrive is NOT primary master, but SATA1 the install can't find it.I am a complete newbie to Linux. Hoe do I mount the hd?

---

### Post by Pumalite on 2008-03-02
Make your BIOS see your SATA as IDE. (maybe disabling the SATA controller)

---

### Post by copan1122 on 2008-03-04
Unfortunately this reply did not work. My motherboard documentation show that the SATA connections (I have two) are separate from the IDE connection. So, disableing SATA won't fix the problem. I might be able to open the box and connect the hd to the IDE connector, but then I lose the advantages of SATA. I'll save that as a last resort.

Also, looking through other problems and fixes. I don't have an enable RAID setting in BIOS. That seems to fix problems for some people.

I keep looking.

---

### Post by dstew on 2008-03-04
Is the 6.10 CD a Live CD, or an alternate install (text-based) CD?

---

