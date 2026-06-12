---
title: "Migrate from 2 disks + OS disk to 5 disk raid 5 + OS disk"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by doomstone on 2010-05-31
Hello forum

I wanted to expand my server&#8217;s capacity and security by upgrading from 2 data disk to 5 data disks in raid 5.

At the moment do i have:
1 OS disk (500Gb)
  - ext4 (6Gb)
  - linux-swap (2 Gb)
  - lvm2 (445.27 Gb)
2 Data Disk (2x1.5Tb)
  - lvm2 (1.5Tbx2)

Now i have bought 3 more 1.5Tb disks and i want to make a Raid 5 with the 5x1.5Tb disks.
But i have hidden a snag here, because i was told that i could just create a raid 5 with the 3 new disks, create a volume there that can handle expanding disk space, example ext4. Then move the data from the 2 old disks to this new volume, and when it is done, add the 2 old disk to the raid volume.

But now that i have the disks do i have some problems finding out who i will be able to extend a raid volumes. So my question is my plan even possible or have i been led astray? If not are there another way i can solve this little puzzle?
There are currently 2Tb data on the 2 disks and i have no other computer with that amount of disk space, so taking a backup on another computer is out of the question :(

My Motherboard is GA-EP35C-DS3R (rev. 2.1)

---

