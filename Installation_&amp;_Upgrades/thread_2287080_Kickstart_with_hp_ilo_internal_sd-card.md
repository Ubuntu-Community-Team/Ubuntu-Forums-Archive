---
title: "Kickstart with hp ilo internal sd-card"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by Jason_S._Evans on 2015-07-16
I'm trying to set up kickstart to be able to install 14.04 on this server, but it always sees /dev/sda as "hp ilo internal sd-card" it will not automatically install on sdb even when I specifically tell it to.

For example:

#ignore /dev/sda
 ignoredisk --only-use=sdb


clearpart --all --initlabel
part /boot --ondisk=sda --fstype ext3 --grow
part pv.01 --ondisk=sdb --size=0 --grow
volgroup vg0 pv.01
logvol swap --fstype swap --name=swap --vgname=vg0 --recommended
logvol / --fstype ext3 --name=root --vgname=vg0 --size=20480 --grow

---

