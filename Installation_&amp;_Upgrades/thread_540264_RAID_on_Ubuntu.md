---
title: "RAID on Ubuntu"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by tnats on 2007-09-01
Ok, I have a current RAID1 setup using 2 300GB disks.

I want to wipe it and add 2 more 300gb disks using RAID 5.

I pop the feisty cd in there and reboot. I get to partitioner and it sees the 4 disks. I set each one up with 298gb of raid along with 2gb of raid swap.

I then go to configure raid and for some reason, my two previous MD devices are already there. I try to delete them but it won't let me. I hit esc, and it brings me back to the partitioner and all of a sudden, my old RAID1 disks are there. I delete those partitions and go back into software raid those MD devices are still there and it gives me the same error when I try to delete the MD devices.

Blech, what am I missing here? Is there somehow a way to 'wipe' the previous MD devices?

Thanks for any help,
Tom

---

### Post by wolfen69 on 2007-09-01
this may help: [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by tnats on 2007-09-01
Actually, that confuses me. I got software raid running with no problems without doing all the special stuff he does in that how-to.

The only issue I'm having is getting rid of the old raid 1 setup.

---

### Post by tnats on 2007-09-03
I figured it out. I had to clear the previous raid setup.

I first did a mdadm -S /dev/md0

Then:
Clearing any previous raid info on a disk (eg. reusing a disk from another decommissioned raid array)

# mdadm --zero-superblock /dev/hdc1


and now it's all clear

---

