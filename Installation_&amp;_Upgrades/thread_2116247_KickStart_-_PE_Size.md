---
title: "KickStart - PE Size"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by piriton on 2013-02-15
When I KickStart my OS, I receive the error message :

```

Could not allocate requested partitions:
not enough space for LVM requests.
Press 'OK' to exit the installer.

```

```

clearpart --drives=sda --all

part /boot --fstype=ext4 --size=4000
part pv.008002 --grow --size=200

volgroup vg00 --pesize=4096 pv.008002
logvol / --fstype=ext4 --name=lv_root --vgname=vg00 --size=94396
logvol swap --name=lv_swap --vgname=vg00 --size=4000

```The PE Size is 4096kb.

The size in total of the PE's comes to :
```

4000
200
94396
4000

= 102596 Physical Extents

```Questions :

1.  The pesize option is specified after /boot.  Does /boot use a PE size of 4096kb.
2.  If the total PE is 102596 (4000 + 200 + 94396 + 4000 ), then how do I convert this to MB or GB because my disk size is 40GB.

---

### Post by piriton on 2013-02-16
Answer : All sizes are in MB, pv size is too small, also minus 1 PE for LVM overhead.

---

