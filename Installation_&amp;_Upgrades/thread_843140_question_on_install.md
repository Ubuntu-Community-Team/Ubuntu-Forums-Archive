---
title: "question on install"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Juggalowang on 2008-06-28
okay im haveing a problem i want to install ubuntu with nothing else i go through the install guide i choose guided i choose entire disk i fill out the other info it wants and when it starts it gets to 15% stops give's me this error message

"The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."

and it kicks me back to step 4

am i doing something wrong or missing something obvious i'm very new to this so its possable

---

### Post by Partyboi2 on 2008-06-28
Try to manually create the partitions with gparted. (System>Admin>Partition Editor) fom the live cd. You will need a / (root) partition for the system file a /swap partition and I recommend a /home partition for your data.

---

