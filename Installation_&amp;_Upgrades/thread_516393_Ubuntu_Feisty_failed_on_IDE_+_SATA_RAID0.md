---
title: "Ubuntu Feisty failed on IDE + SATA RAID0"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by Hanselang on 2007-08-03
Ubuntu 1  vs  Abit AN52 0

Abit AN52 mainboard was a casualty in the quest for SATA RAID0 dual boot WINXP and Ubuntu.
Followed both the Ubuntu Wiki Howto:FakeRaid quite successfully. (1 day trying the 'easy way' post in Install Forums as well as understanding the terminology and that if Ubuntu can't read the partition, ITS NOT LOADED STUPID(me))

However, the GRUB window failed to appear at the next reboot, and went into Windows, next try using LIVECD.

After Gparted failed to partition my IDE 200GB HDD (spent few min before shutting down), I chose to RESTART. Bad move.
Upon waiting for the POST screen, I hit the reset button (thinking Ubuntu failed to restart), then...

[B]NO POST SCREEN[/B (monitor still works)]
Next steps:
1. Clear power on Powersupply
2. Reset(clear) BIOS
3. Unplugged all drives and memory and clear BIOS
4. Power up beep but still nothing...


Sent the PC into servicing... Good thing this is new with 1-to-1 exchange...

---

### Post by Hanselang on 2007-08-03
Nevermind.

Ubuntu fails because of this.
A home is worthless if one cannot enter it.

Thank you and please lock this post.

---

