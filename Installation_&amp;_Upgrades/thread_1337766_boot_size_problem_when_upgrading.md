---
title: "/boot size problem when upgrading"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by adana on 2009-11-25
I am upgrading from 8.04 to 8.10 and getting the message that my /boot is too small. It's 228m.

I have tried gparted from the liveCD but it doesn't seem to see my filesystems. Also I hear that I may have UUID problems?


My filesystems are:

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                      110G   66G   39G  64% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   68K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   40M  466M   8% /lib/modules/2.6.24-25-386/volatile
/dev/sda1             228M   16M  201M   8% /boot


Can anyone advise?

---

### Post by adana on 2009-11-25
Here is more info about my system:


Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000354cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       14946   119804737+   5  Extended
/dev/sda5              32       14946   119804706   8e  Linux LVM

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15362b52

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          17      136521   83  Linux
/dev/sdb2              18       18254   146488702+  83  Linux
/dev/sdb3           18255       38913   165943417+  83  Linux

---

