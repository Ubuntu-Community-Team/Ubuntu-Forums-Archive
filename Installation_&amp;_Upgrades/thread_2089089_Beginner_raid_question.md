---
title: "Beginner raid question"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by jonas82swe on 2012-11-28
[SIZE=3][FONT=Calibri]I have a beginner question about using software raid on Ubuntu and what the smartest way is to build the hardware for a home-file-server.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]My plan is to have a server with one system disk(SSD 60GB) and 3-6 2TB disks in a software raid 5 or 6 or 10(haven’t decided yet...) using mdadm. So my idea is to not include the SSD drive in any raid, and just run it standalone with Ubuntu server. [/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Anyhow, let’s say that I create a raid5 with four disks. After a awhile the SSD crash(as I probably will do after a couple of years). What will then happen with my raid 5? [/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Will I be able to buy a new “system disk” and just install a fresh Ubuntu version + mdadm and then the system just recognize my old raid5 that was built on the old crashed Ubuntu? Or should I start to cry ;-) because my raid5 is gone? Maybe there are some checksum or similar(I don’t know software raid 5 works…) that are needed from the old crashed Ubuntu to recognize the raid5?[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]The reason to why I want to have separate system disk is because I want a fast disk for the system and separate the file storage on separate disks that are bigger(and slower) but cheaper :)). Also, if not really really necessary I want to avoid using two SSD in a raid as system disk(disk are expensive). [/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I want to keep my system as simple as possible so I want to avoid the need to take system backup(like snapshots). The server is only for home use so I doesn’t matter if I have a downtime of a couple days, and installing Ubuntu again from the beginning is simple and not so time consuming. The most important is that I can connected the raid5 to the new freshly installed Ubuntu. [/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Many thanks in advance for your help![/FONT][/SIZE]

---

### Post by Cheesemill on 2012-11-28
All of the RAID information is on the storage drives, you can do a new installation or even move the storage drives to a different machine and the RAID will work just fine.

One thing to point out is that RAID is not a backup solution, it's a continuity plan that only protects against drive failure.

You should always keep a proper backup of your data as well as using RAID.

---

### Post by jonas82swe on 2012-11-28
> **Cheesemill said:**
> All of the RAID information is on the storage drives, you can do a new installation or even move the storage drives to a different machine and the RAID will work just fine.
 
One thing to point out is that RAID is not a backup solution, it's a continuity plan that only protects against drive failure.
 
You should always keep a proper backup of your data as well as using RAID.
 
[SIZE=3][FONT=Calibri]Thank you very much for your reply. [/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]A ha, I see, great news that the raid information is on the storage drives. Then my idea will work for my user case.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]- I recently learned that when reading about different how-to about raid , the reason to why I want to use raid except for continuity is simply by practical and convenient reasons(to have a big storage location instead of spreading files on different HD).[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Thanks again.[/FONT][/SIZE]

---

