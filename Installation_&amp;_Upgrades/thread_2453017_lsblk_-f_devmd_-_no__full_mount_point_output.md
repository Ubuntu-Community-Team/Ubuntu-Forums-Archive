---
title: "lsblk -f /dev/md* - no  full mount point output"
date: 2020-11-01
forum: Installation &amp; Upgrades
---

### Post by helen314 on 2020-11-01
lsblk -f /dev/md1 command gives full mount point  data 


lsblk -f /dev/md* DOERS NOT gives full mount point  data 


**Is there a way to correct this ? **

```

f@f-SATA:~$ lsblk -f /dev/md1
NAME    FSTYPE LABEL           UUID                                 MOUNTPOINT
md1                                                                 
&#9500;&#9472;md1p3 ext4   MISC_COPY_LABEL 922f42e6-6ab1-4cd0-bc82-2aee9868187f /mnt/922f42e6-6ab1-4cd0-bc82-2aee9868187f
&#9500;&#9472;md1p1 ext4   DOC_COPY_LABEL  92f91148-a6dd-4d06-9276-83ba2e39ec07 /mnt/92f91148-a6dd-4d06-9276-83ba2e39ec07
&#9500;&#9472;md1p4 ext4   BACK_COPY_LABEL a1a4ce77-11ca-439c-ac63-a897e5d2896b /mnt/a1a4ce77-11ca-439c-ac63-a897e5d2896b
&#9492;&#9472;md1p2 ext4   DEV_COPY_LABEL  506d7ca6-b09c-415b-a681-f7f71ec62513 /media/f/DEV_COPY_LABEL
f@f-SATA:~$ lsblk -f /dev/md*
lsblk: /dev/md: not a block device
NAME      FSTYPE LABEL           UUID                                 MOUNTPOINT
md1                                                                   
&#9500;&#9472;md1p3   ext4   MISC_COPY_LABEL 922f42e6-6ab1-4cd0-bc82-2aee9868187f /mnt/922f4
&#9500;&#9472;md1p1   ext4   DOC_COPY_LABEL  92f91148-a6dd-4d06-9276-83ba2e39ec07 /mnt/92f91
&#9500;&#9472;md1p4   ext4   BACK_COPY_LABEL a1a4ce77-11ca-439c-ac63-a897e5d2896b /mnt/a1a4c
&#9492;&#9472;md1p2   ext4   DEV_COPY_LABEL  506d7ca6-b09c-415b-a681-f7f71ec62513 /media/f/D



```

---

### Post by GhX6GZMB on 2020-11-01
Dunno how you got the idea that * is a valid joker for lsblk. "man lsblk" does not mention this.
Your first command is OK, the second just ignores the /dev/md* part and lists what you have. Operator error, I'd say.

---

