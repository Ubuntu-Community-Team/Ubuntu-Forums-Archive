---
title: "LVM Snapshot before Unattended Updates"
date: 2019-07-03
forum: Installation &amp; Upgrades
---

### Post by mauzaritta3 on 2019-07-03
Hello, 

I would like to create a LVM Snapshot before Ubuntu uses it unattended Update feature. My first idea was to add the snapshot command to a new created file 49beforeunattended in /etc/apt/apt.conf.d but for me the files in /etc/apt/apt.conf.d looks more like configuration files where a bash script will not work.

Does anyone had the same requirement ?


Best Regards Marc

---

### Post by TheFu on 2019-07-03
Snapshots are part of my backup process.  Cat5.tv did 3 episodes about LVM, snapshots and backups that you might find useful a few years ago.  Sorry, I don't know the exact episodes, but finding them should be easy on youtube.

Snapshots don't replace the need for backups.  They are just like RAID in that regard. 

And don't forget that snapshots aren't meant to be forever. You are supposed to create them, use them for a day or week, then delete the snapshot.  Remember how snapshots actually work. They freeze file system blocks from modification, so the size of the snapshot needs to be sufficient to hold any new changes.

---

### Post by mauzaritta3 on 2019-07-04
Hello TheFu,

> Snapshots don't replace the need for backups.  They are just like RAID in that regard.

True, Snapshots don't replace the backup. The idea is more likely the following:

- Create an automatic snapshot before automatic update
- Automatic update via Ubuntu unattended update
- Manually check the system for problems
- Delete Snapshot at the same day.

BR Marc

---

