---
title: "Ubuntu installed, cannot see other partitions"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by HeZ on 2010-11-25
Hi i have just installed Ubuntu on my laptop. The hard drive i installed on was partitioned in half, proir to install one of those partitions had windows on it, the other is for data and such.

I installed on (and formatted) the partition with windows, now Ubuntu loads fine and all is good but i cannot see that second partition with data.
Do i have to install it or something?

Thanks 
HeZ

---

### Post by HeZ on 2010-11-25
Ahh nevermind i found the Disk Utility.
Can i choose where i want to mount it tho, it automatically mounts it in /media

---

### Post by theskipirate on 2010-11-25
Have a look at my thread, seems we are having the same problem...

[http://ubuntuforums.org/showthread.php?t=1630097](http://ubuntuforums.org/showthread.php?t=1630097)

---

### Post by HeZ on 2010-11-25
I was able to install on that partition tho. Seems once you get Ubuntu installed you have to mount any other partitions.
Do that from System>Administration>Disk Utility

---

### Post by sikander3786 on 2010-11-25
> **HeZ said:**
> I was able to install on that partition tho. Seems once you get Ubuntu installed you have to mount any other partitions.
Do that from System>Administration>Disk Utility
In order to mount those partitions permanently, you need to define the mount points in fstab.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Or if they are formatted NTFS, you can use a gui tool for that called NTFS Config Tool. Search Software Center for that.

If you need further help, please post the output of these commands.

```
sudo fdisk -l
```

```
sudo blkid
```

```
cat /etc/fstab
```

---

