---
title: "RAID Partitioning"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by lynwode on 2008-08-10
Having had a disaster upgrading from Gutsy to Hardy I have made the decision to reinstall Gutsy.

I have also decided to go RAID. I am trying to set up RAID via the installer however I am unsure of what structure the partitions should take and in what step to create things. Also where does LVM come into the mix?

I have 4 x 320GB SATA drives that I would like to set up as RAID 5. Can anyone provide any ideas of how I shoudl go about this.

Cheers,
Tim.

---

### Post by pparks1 on 2008-08-10
Well, first things first.  You don't want to install your operating system onto a RAID 5 array.   If you are doing a software based RAID, it likely won't even allow this.     You do NOT want your system calculating parity for temporary files, etc.

I would seriously install 2 x XXGB drives in a RAID1 mirror for the OS and then use the 4 x XXGB drives in a RAID5 array for data.

LVM is logical volume management.   The benefits here is that you can keep adding on disk space onto a volume and grow the volume as need be.  However, there isn't fault tolerance by default with LVM's.   You are just more or less pasting hard drives together to present 1 large volume with an LVM.

---

### Post by lynwode on 2008-08-10
Thanks for your response. 

If I were to go down the track you suggested how would I set this configuration up in the installer?

Tim

---

