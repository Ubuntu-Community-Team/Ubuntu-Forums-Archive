---
title: "Dual booting from different hard disks"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by DR_D` on 2007-01-26
i'm trying to install ubuntu onto a spare HD in my XP machine.

My hard disk setup is show below along with the locations of the OS's and GRUB.

IDE 1 Master : 120Gb HD  <---- Grub installed here by ubuntu
IDE 1 Slave : 160GB HD
IDE 2 Master : 200GB HD  <----- Ubuntu installed here
IDE 2 Slave : DVDRW
IDE RAID 1 Master : 160GB HD
IDE RAID 1 Slave : 160GB HD
SATA 0 : 36GB HD   <------ XP installed here
SATA 1 : 300GB HD

The problem i'm getting is when i set IDE 1 Master to boot, as you would seeing as grub is there, i get an error 17 from grub.

Setting SATA 0 to boot and xp starts up.

What am i missing?

---

### Post by PriceChild on 2007-01-26
Grub isn't actually installed on a separate partition...
The starting up bit is written to the mbr before the partitions, and then everything else is inside where you installed Ubuntu, unless you specified a different /boot partition.

Try setting IDE master 2 to boot and see what happens.

If not then we can just reinstall grub :)

---

### Post by DR_D` on 2007-01-26
i have tried that and got an error can't remember what it said. i'll find out if needed but the main thing is it didn't even start to boot

---

### Post by PriceChild on 2007-01-26
I'd advise reinstalling grub: [http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

---

### Post by DR_D` on 2007-01-26
so from that link you just posted, what would i put in the "root" and "setup" commands?

and would the xp hd be added to grub automatically?

---

### Post by DR_D` on 2007-01-28
Okay i've now managed to get ubuntu to boot via grub by disconnecting all HD's except the one ubuntu was installed too and reinstallled grub. Now i need to edit the grub menu so i can dual boot to XP.

below is the output from fdisk -l

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14946   120053713+   7  HPFS/NTFS

Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       24036   193069138+  83  Linux
/dev/hdc2           24037       24792     6072570    5  Extended
/dev/hdc5           24037       24792     6072538+  82  Linux swap / Solaris

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4499    36138186    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       19457   156288321    7  HPFS/NTFS
dave@dave-desktop:~$ 21    7  HPFS/NTFS
dave@dave-desktop:~$ 
```

grub and ubuntu are on HDC whilst the xp partion is on sda.

What do i need to add to the /boot/grub/menu.lst file?

---

### Post by DR_D` on 2007-02-04
bump

---

