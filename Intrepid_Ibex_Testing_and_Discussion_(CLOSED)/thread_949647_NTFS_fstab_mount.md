---
title: "NTFS fstab mount"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2008-10-16
I did a upgrade and ,later, a clean install and intrepid didn't mount my NTFS drives.

Could somebody share their fstab if they have NTFS drives mounted?

Here is my NTFS entry. Is this ok or should i change it to something else? 

#Jupiter
/dev/sda1 /media/Jupiter ntfs-3g user,defaults 0 0

---

### Post by bash on 2008-10-16
Two questions come to mind:
1. What happens if you manually mount the drive? Maybe the NTFS wasn't cleanly unmounted and is now flagged.
2. You made sure the folder /media/Jupiter exists?

---

### Post by zekopeko on 2008-10-16
everything works fine. the disk is mounted and works.i was just wondering if i used the right options.
like should i use ntfs-3g for the filesystem driver or something else. Gnome system monitor says that the drive is mounted with fuseblk so that's confusing.

---

### Post by nanog on 2008-10-16
```
/dev/sdc1 /media/devicename ntfs-3g defaults,force 0 0 
```
Yours looks fine. I add the force option only because I've found ntfs can be a bit balky sometimes. This works for me on servers and desktops.

---

### Post by Kow on 2008-10-16
> **nanog said:**
> ```
/dev/sdc1 /media/devicename ntfs-3g defaults,force 0 0 
```
Yours looks fine. I add the force option only because I've found ntfs can be a bit balky sometimes. This works for me on servers and desktops.

I would not recommend forcing the mount. If the NTFS drive is flagged (marked dirty) it NEEDS to be checked by the Microsoft Disk Checker (NOT ntfsfix!!) otherwise you could easily corrupt the entire filesystem and lose all data on it. I have 2 NTFS partitions and they have been only marked dirty once by Ubuntu... when I lost electricity. I first ran ntfsfix on it and then rebooted to Windows which found a million more errors than what ntfsfix did.

Conclusion:
(1) NEVER put a force option in fstab
(2) NEVER use ntfsfix alone
(3) ALWAYS check with Microsoft's chkdsk if the filesystem is flagged.

---

