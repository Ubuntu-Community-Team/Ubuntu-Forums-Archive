---
title: "Cant access hard-disks on the computer"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by bjluv on 2006-09-10
I do need helps regarding Ubuntu Linux.

I reformatted my hard-disk and istalled my Windows XP Pro back with Ubuntu Linux 6.06 on the C: drive. 

Now when I boot into Linux and want to access my other hard disk which I use for storage [i have 2 hard disk on the computer] I get this error:-

```
Unable to mount the selected volume.
>Show more _d_etails

error: device /dev/hda1 is not removable

error: could not execute pmount
```

Can you please be of help and let me know how to solve this? I can only open the **File System**


thnx for your reply...

---

### Post by meng on 2006-09-10
Windows drives will not automatically mount by default. Check out this wiki:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by bjluv on 2006-09-10
so how can I mouth  the drives and I can read & write files to the disk please...

---

### Post by meng on 2006-09-10
It's explained in the link, no? Also note that write-access to NTFS partitions is (I understand) still experimental.

---

### Post by bjluv on 2006-09-10
thnx for the info but i did everything on steps 1-5
> [https://help.ubuntu.com/community/MountingWindowsPartitions#head-7036f2492d04f1d0984017ad8e71af0eda2690d6](https://help.ubuntu.com/community/MountingWindowsPartitions#head-7036f2492d04f1d0984017ad8e71af0eda2690d6)

and still i cant access the partitions.


It shows:-
> **The folder contents could not be displayed.**
You do not have the permissions necessary to view the contents of "disks-conf-hdb5".


Do you think that item 3. Accessing the Files on Your Windows Partition From Ubuntu might help?


Can this mean that many people are not using their Windows Partition From Ubuntu? :)

---

### Post by bjluv on 2006-09-10
> **meng said:**
> o? Also note that write-access to NTFS partitions is (I understand) still experimental.

well yeah it would be just nice if I can read from WINDOWS when I want...

---

### Post by meng on 2006-09-10
I think the "accessing files ..." section may indeed help you, if you look at the later section on mounting NTFS with read support only, as a safer starting point. I no longer use Windows, so I am unfamiliar with these techniques myself.

---

