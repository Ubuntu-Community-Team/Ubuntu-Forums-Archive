---
title: "back up user accounts befor reformat"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by dennisofnewport on 2012-08-23
OK this I do not understand. I want to back up a user file that is different the mine. I am log on as administrator, when I drag the folder named JUDY to the back up drive it tells me I can not do this because I am not the owner.

Judy's account will not allow me to access the back up drive. So I can not back up from her account. 

Any suggestions on how to perform a data backup on both my user account and hers, I want to reformat the main drive.

---

### Post by TheFu on 2012-08-23
You want to backup the system/files using "root" (or sudo).  There may be a way to do this with a GUI, I just don't know it.  If you use a normal backup tool, this and the restore later will be easier.
* DejaDup
* Duplicity
* Duplicati
* rdiff-backup
* Back-in-Time (best run by end-users, not root)
There must be hundreds of others.

Backing up the data files is not necessarily enough. You probably want to backup the permissions and and ACLs too.  For this to work, you need storage to be able to handle those permissions. NTFS and other non-Linux file systems are most likely not good enough to backup this other data.

An easier way for next time is to have 2 partitions
* OS/Apps
* Home
When it is time to upgrade the OS/Apps, your HOME directories are not impacted.

Using rdiff-backup is how I do it. Nightly and automatic retaining 30-60 days of backups.

---

### Post by Bashing-om on 2012-08-23
Dennis;

  Try this and see if it works:
```
gksudo nautilus
```
drag and drop----
root privileges from the application level should work.

[INDENT]HTH >==BDQ
[/INDENT]

---

### Post by Bucky Ball on 2012-08-23
> **Bashing-om said:**
> Dennis;

  Try this and see if it works:
```
gksudo nautilus
```drag and drop----


+1. Replace Nautilus with 'Thunar' or whatever else you happen to be using if it's not Nautilus.

---

