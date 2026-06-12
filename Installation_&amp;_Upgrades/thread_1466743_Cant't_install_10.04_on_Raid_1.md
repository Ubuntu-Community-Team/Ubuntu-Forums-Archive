---
title: "Cant't install 10.04 on Raid 1"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by dirtydave on 2010-04-30
Having trouble installing 10.04 on sata raid 1.  I have even tried the alternate install cd, errors out at (failed to create file system)  -- The ext4 file system created in partition #1 of Serial ATA RAID pdc_fefbcjfbc (mirror) failed.
                 I'm not sure where to go from here?

---

### Post by psusi on 2010-04-30
You are affected by this bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050)

Try to manually configure the partitions with gparted, then install and use the existing partitions.  gparted also does not show fakeraid partitions in its drop down list in lucid so you will need to run it from the command line and specify the raid device to use.

sudo gparted /dev/mapper/pdc_fefbcjfbc

By the way, unless you are dual booting with windows you should not be using the fake raid support.  It does not handle errors properly.  Use linux software raid instead.

---

