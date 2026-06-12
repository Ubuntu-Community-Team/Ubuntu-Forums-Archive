---
title: "Uninstallation of dual boot Ubuntu  - which partitions to delete."
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by jmvizanko on 2011-10-02
I am currently running dual boot of Ubuntu 11.04 and Windows 7 on a Samsung RC512 with a 750GB ATA HD.  The initial install of Ubuntu was done using an Ubuntu 10.10 CD, and I used the auto repartitioning built into that installation (I know, the sloppy lazy way to do it...)

I now would like to remove Ubuntu and get it back to a Windows only machine.  I plan on deleting the Ubuntu partitions in Windows, repairing the boot using my Windows CD, and then transferring the space back to my C drive in Windows.

In Ubuntu 11.04 I see the following volumes from left to right.

SYSTEM 105 MB NT... (this volume is gray in color, the rest are white)
291 GB NTFS
Extended 430 GB   (under which are the following 3)
         ___225 GB NTFS
         ___205 GB ext4
         ___6.3 GB Swa... 6.3 GB
SAMSUNG_REC 23 GB NTFS

In Windows 7, I see the following in Disk Management (all are Simple for Layout and Basic for Type).

Volume: -
File System: -
Status: Healthy (Primary Partition)
Capacity: 190.89 GB

Volume: -
File System: -
Status: Healthy (Primary Partition)
Capacity: 5.86 GB

Volume: -
File System: -
Status: Healthy (Recovery Partition)
Capacity: 21.37GB

Volume: (C:)
File System: NTFS
Status: Healthy (Boot, Page File, Crash Dump, Primary Partition)
Capacity: 271.00 GB

Volume: (D:) 
File System: NTFS
Status: Healthy (Logical Drive)
Capacity: 209.41 GB

Volume: SYSTEM
File System: NTFS
Status: Healthy (System, Active, Primary Partition)
Capacity: 100 MB

So which ones should I blow away, or is there a much easier way to do this (like a just as sloppy and lazy automatic uninstallation repartitioning tool (clearly I don't know enough to have ever even bothered with the OS))?  Thanks for any help as always.

---

### Post by Blasphemist on 2011-10-02
> **jmvizanko said:**
> I am currently running dual boot of Ubuntu 11.04 and Windows 7 on a Samsung RC512 with a 750GB ATA HD.  The initial install of Ubuntu was done using an Ubuntu 10.10 CD, and I used the auto repartitioning built into that installation (I know, the sloppy lazy way to do it...)

I now would like to remove Ubuntu and get it back to a Windows only machine.  I plan on deleting the Ubuntu partitions in Windows, repairing the boot using my Windows CD, and then transferring the space back to my C drive in Windows.

In Ubuntu 11.04 I see the following volumes from left to right.

SYSTEM 105 MB NT... (this volume is gray in color, the rest are white)
291 GB NTFS
Extended 430 GB   (under which are the following 3)
         ___225 GB NTFS
         ___[COLOR="Red"]205 GB ext4
         ___6.3 GB Swa... 6.3 GB[/COLOR]
SAMSUNG_REC 23 GB NTFS

In Windows 7, I see the following in Disk Management (all are Simple for Layout and Basic for Type).

Volume: -
File System: -
Status: Healthy (Primary Partition)
Capacity: 190.89 GB

Volume: -
File System: -
Status: Healthy (Primary Partition)
Capacity: 5.86 GB

Volume: -
File System: -
Status: Healthy (Recovery Partition)
Capacity: 21.37GB

Volume: (C:)
File System: NTFS
Status: Healthy (Boot, Page File, Crash Dump, Primary Partition)
Capacity: 271.00 GB

Volume: (D:) 
File System: NTFS
Status: Healthy (Logical Drive)
Capacity: 209.41 GB

Volume: SYSTEM
File System: NTFS
Status: Healthy (System, Active, Primary Partition)
Capacity: 100 MB

So which ones should I blow away, or is there a much easier way to do this (like a just as sloppy and lazy automatic uninstallation repartitioning tool (clearly I don't know enough to have ever even bothered with the OS))?  Thanks for any help as always.
Windows isn't showing you the partitions accurately. I'd boot the ubuntu live cd and run GParted to delete the right partitions. They are both logical partitions within the extended partition and from above using linux, they show as what I made red.

---

