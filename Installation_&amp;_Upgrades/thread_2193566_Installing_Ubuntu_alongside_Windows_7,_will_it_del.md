---
title: "Installing Ubuntu alongside Windows 7, will it delete files?"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by bigtinyman on 2013-12-13
Hi all,

I want install Ubuntu alongside Windows 7 on my SSD. However, my drive only has one partition with Windows 7 on it. When I install Ubuntu and choose the option to partition the drive and install it on the new partition, I'm wondering if the partition process will delete everything on the drive? In other words, will I lose everything I had on Windows 7? 

Thanks!

---

### Post by MG&amp;TL on 2013-12-13
No, you won't. Multiple operating systems can and do co-exist on the same disk or machine quite happily. That said, partitioning is quite an art in itself, so I would recommend reading at least some of the [HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition") guide, even if you let the installer do it for you.

Also, things do (albeit rarely) go wrong, so I suggest having a backup of your important files in the event of an emergency *before* you run the installer.

---

### Post by oldfred on 2013-12-13
I like to partition in advance. Then I know exactly which partition is which and what size it is, not some auto default. Also then you have the option with manual install or Something Else of adding separate partition like /home if desired.

We occasionally see users who chose the wrong install option. The install to entire drive means in Linux the entire physical drive, not a Windows definition where a drive is a partition.  Or it does erase everything.
The new installer is not clear that the LVM options mean entire drive also. The old alternative installer always said entire drive and most users that want LVM know that.

---

