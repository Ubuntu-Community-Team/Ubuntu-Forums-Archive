---
title: "/home/user on a different partition"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by jasonlfunk on 2007-02-10
I want to have my user's home directory on a different partition then my root partition but I cannot seem to get it to mount with the correct permissions. This is what I currently have in my fstab.

```
/dev/sda3     /home/funkja/   vfat    defaults,uid=funkja,umask=0002,gid=funkja       0       0
```

What am I missing?

---

### Post by jasonlfunk on 2007-02-10
After reading a little bit more, is it more common to mount the different partition to /home/ instead of to /home/user?

---

### Post by Irony on 2007-02-10
The format should be something like;

[PHP]/dev/sda3	/home		ext3    defaults        1       2[/PHP]

I assume you've copied over your home partition and then renamed your current home partition to something like home_backup and then made another folder called home.

Note you can't have home on a vfat partition as it doesn't recognise permissions.

---

### Post by jasonlfunk on 2007-02-10
I guess my problem is having the vfat partition. Guess I will have to reformat.

---

