---
title: "Disk freeze after upgrade to 8.10"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by piloupuc on 2008-11-03
I have 2 disks: disk 1 has 4 partitions: sda1 (ntfs), sda2 (Linux), sda3 (extended) and sda5 (linux-swap)
disk 2 has 2 partitions: sdb1 (ntfs) used for windows system and sdb2 (ntfs) used for data (with access both from ubuntu and windows)

Since I upgraded to 8.10 it looks as if sdb2 partition is corrupt. nautilus,rythmbox, etc, freeze when I access data on sdb2 and I can't write anything anymore, then I can't shut down properly). 
The problem is, this is where I store most of my data, so I can access it both from ubuntu and from windows (xp).

I ran the Maxtor disk-checking tools and everything was OK.
Also, when I boot from the windows side I get no errors with the disk (and chkdsk can't find anything wrong with the drive).
I even reformated the problematic drive, but the problems remain.

Not sure what to do next... Any ideas?

---

### Post by Partyboi2 on 2008-11-03
you could try running fsck the next time you boot
Open a terminal and type
```
sudo touch /forcefsck
``` then reboot.

---

### Post by piloupuc on 2008-11-03
The thing is, running a fsck at boot checks the drive that runs ubuntu (sda2 in my case) and there is no problem with it. The problem is with the NTFS partition where I store documents (sdb2).

---

### Post by piloupuc on 2008-11-03
> **Partyboi2 said:**
> you could try running fsck the next time you boot
Open a terminal and type
```
sudo touch /forcefsck
``` then reboot.

Thanks for the reply!
The thing is, running a fsck at boot checks the drive that runs ubuntu (sda2 in my case) and there is no problem with it. The problem is with the NTFS partition where I store documents (sdb2).

---

