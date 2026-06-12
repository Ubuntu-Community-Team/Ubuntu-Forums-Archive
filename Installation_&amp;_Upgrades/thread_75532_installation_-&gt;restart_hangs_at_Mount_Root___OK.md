---
title: "installation -&gt;restart hangs at Mount Root :  OK"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by xolot1 on 2005-10-13
ive been excited about today for a while.

when i heard ubuntu was coming out the same day i had no school, my plans were made.  after Ubuntu died (b/c of me screwing around with it) last week, i starting using knoppix dvd until the upgrade came out.  i really liked the KDE, so decided to try kubuntu.

i dled it this morning, and then spend much of the afternoon trying to get it to work.  after varying degrees of success, i come to you guys.

right now:
ive gone through the first part of the install.  all the info/packages were transferred to my harddrive seamlessly.  my comp restarted, found all my devices, grub loaded, started kubuntu.

pretty kubuntu logo appeared, and under it said (to this effect):
loading modules   ok
initializing /dev  ok
mounting root  ok
** then it stops**

first time it happened, i left it and took a shower, came back, and the screen was unchanged.

i re-reinstalled up the the same point, and here i am again.

any suggestions?
anything data i can gather to help you guys out?
thanks for helping, i know there are alot of other threads you could be responding to instead of mine.

---

### Post by adwait on 2005-10-13
Maybe theres any error on the root file system? Try booting into single user mode from GRUB, and then mount the / partition readonly. Run fsck on it.

---

