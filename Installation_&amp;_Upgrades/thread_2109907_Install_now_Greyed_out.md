---
title: "Install now Greyed out"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by Elitenoname on 2013-01-28
Trying to install ubuntu and it will not let me click the "install now" button when i select how i want to install ubuntu. it is grayed out for all options, and when i try to setup up the partitions manually it is still grayed out. anyone ran into this or have any idea why it is doing this?

---

### Post by oldfred on 2013-01-30
From liveCD/DVD/Flash open gparted. Does it show existing partitions? It may have yellow or red icons and give a little more info on issues.

Was drive ever RAID or do you have Intel SRT which uses RAID?
Did you use Windows to create more than 4 partitions and it converted from basic to dynamic?
Does NTFS partition need chkdsk?

Those are  main reason why drive will not be shown.

Post this:

sudo fdisk -lu
       sudo parted /dev/sda unit s print

---

