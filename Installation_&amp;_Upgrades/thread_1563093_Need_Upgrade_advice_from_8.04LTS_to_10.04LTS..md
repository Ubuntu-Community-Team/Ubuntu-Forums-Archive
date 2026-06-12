---
title: "Need Upgrade advice from 8.04LTS to 10.04LTS."
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by Linuxer on 2010-08-28
I have a stable 8.04LTS installation on my desktop (home built) that has been running for the past 2 years without any problems.  I know the support for 8.04LTS goes away next year and I see an "Upgrade to 10.04 LTS" option in the update manager.  There appear to be problems following this upgrade path.  Is there an FAQ or an upgrade guide that might ease the transition?

I am running 10.04LTS installed on a USB flashdrive on my Lenovo laptop and would like to upgrade my desktop to 10.04LTS.

Thanks in advance.

---

### Post by wilee-nilee on 2010-08-28
Some have upgraded with no problems, personally I wouldn't, but do a fresh install. The reasons being is the change in grub the bootloader and the move to ext4. Do yourself a favor backup what you want to save, and make sure Lucid runs from a live cd then install.

Upgrades can take much longer, then a fresh install and you could be left with a broken setup. This is especially possible with all the changes that have happened from Hardy to Lucid.

---

### Post by Linuxer on 2010-08-30
Thanks for your suggestion.  I am leaning in that direction, but just wondered if the upgrade process has become smoother.....

Any suggestion for partitions and sizes?

Thanks in advance.

---

### Post by snowpine on 2010-08-30
An upgrade from 8.04 to 10.04 is fully supported following these instructions:

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

Make sure to read through the upgrade notes thoroughly for any "gotcha!"s before proceeding. :) In fact I recommend thoroughly testing a 10.04 Live CD for any bugs/hardware incompatibilities.

---

