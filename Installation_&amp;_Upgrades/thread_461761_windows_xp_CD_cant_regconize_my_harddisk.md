---
title: "windows xp CD cant regconize my harddisk"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by calkelvzeee on 2007-06-02
ok, i have a hp pavilion dv200t with Winxp home, 80GB hdd.
I formatted the harddisk with ubuntu live cd and of coz installed ubuntu 7.04
but later i wish to use dualboot. I put in a windows xp cd, and it says "No harddisk present"
then i try to use win98 fdisk function. it can only regconize 10GB or my harddisk, which is NON-DOS format. then i try to remove grub n blahblahblah, use ubuntu cd to format the hdd as NTFS, all failed
i duno what to do:(:(

---

### Post by ugm6hr on 2007-06-02
> **calkelvzeee said:**
> ok, i have a hp pavilion dv200t with Winxp home, 80GB hdd.
I formatted the harddisk with ubuntu live cd and of coz installed ubuntu 7.04
but later i wish to use dualboot. I put in a windows xp cd, and it says "No harddisk present"
then i try to use win98 fdisk function. it can only regconize 10GB or my harddisk, which is NON-DOS format. then i try to remove grub n blahblahblah, use ubuntu cd to format the hdd as NTFS, all failed
i duno what to do:(:(

Use the GParted LiveCD (or even GParted on Ubuntu LiveCD should work) to create a FAT32 primary partition on your HD. I believe GParted formats partitions by default - but if not, you can use:
```
mkfs.msdos -c -F 32 -n WINDOWS /dev/*partition*
```
Obviously, you will have to substitute *partition* for the intended Windows partition (e.g. hda1)

Then boot from WindowsCD and just select the correct partition - I would suggest you use the WindowsCD to reformat the partition before installing (particularly if you chose NTFS).

PS: Is the 10GB non-DOS partition your system restore?  Does GRUB already give you an extra option other than Ubuntu that might be this restore partition?  If so - you could probably restore by booting from that rather than doing a full re-install.

---

### Post by calkelvzeee on 2007-06-04
i think i removed the system restore already. grub doesnt give any option other than ubuntu

---

