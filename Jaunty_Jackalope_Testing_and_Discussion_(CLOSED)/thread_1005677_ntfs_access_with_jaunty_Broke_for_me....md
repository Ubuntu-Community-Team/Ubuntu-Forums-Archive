---
title: "ntfs access with jaunty? Broke for me..."
date: 2008-12-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by defconoii on 2008-12-08
For some reason when I upgraded to Jaunty I cannot access my wind0ze partition.  I get Cannot get volume.fstype.alternative.  Any ideas on how to fix this?
Thanks
defcon

---

### Post by gthou on 2008-12-08
I confirm I have the same issue when I double click my unmounted windows partition in gnome - "Unable to mount the volume Details: Cannot get volume.fstype.alternative"

I can mount the NTFS volume manually.

---

### Post by gthou on 2008-12-08
Just found a bug filed for this issue:
hal rejects to mount ntfs-3g partition
[https://bugs.launchpad.net/bugs/300443]("https://bugs.launchpad.net/bugs/300443")

---

### Post by dakkar9999 on 2008-12-08
Just did this. According to the instructions and it works.  Not sure if it will remount automatically on reboot...



You have to install ntfs-config to fix this problem:

# apt-get install ntfs-config

Then go to System/Administration/NTFS Config Tool

and voilà !

---

### Post by gthou on 2008-12-09
That tool just offers an alternative way of mounting the partition but does not offer a fix to the bug.

The bug is something internal to gnome and the way it automatically mounts partitions.

---

