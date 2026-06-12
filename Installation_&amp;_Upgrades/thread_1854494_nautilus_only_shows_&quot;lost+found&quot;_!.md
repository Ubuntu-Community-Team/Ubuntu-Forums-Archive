---
title: "nautilus only shows &quot;lost+found&quot; !"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by pijamaz on 2011-10-04
Hi.
 I made a bad  decision when I was installing ubuntu. I assigned one 150 GB partition to "/" and another 150 GB to "/home" I left  a 200 GB partition for storing personal stuff (photos...). I used ext4 file system for all partitions but I cannot work with that partition in nautilus, when I open that partition (in nautilus) a folder appears named "lost+found" and I cannot paste any kind of file there.
Please help me how to use this partition (which I have not assigned it to anything "linux" like "/usr" or "/home") under nautilus. what should I do?
thanks in advance.

---

### Post by drs305 on 2011-10-04
It's probably a permission problem.

If you can see the contents when you run "gksu nautilus" and navigate to the folder, it probably means the mount point is owned by root.

You can change the ownership of the mount point to yourself and the files should be visible the next time the folder is mounted. You can change permissions while in nautilus as root (with the above command) by right clicking on the folder, selecting Properties, then Permissions. Or you can use the 'chown' command from a terminal. Just be careful that if you do a universal chown that it is of the data file and not your system folders.

If you need help with the commands and it is a permission problem, we can help if you provide the mount point of your data partition (e.g. /mnt/mydata, /media/mydata, etc).

---

### Post by pijamaz on 2011-10-04
> **drs305 said:**
> It's probably a permission problem.

If you can see the contents when you run "gksu nautilus" and navigate to the folder, it probably means the mount point is owned by root.

You can change the ownership of the mount point to yourself and the files should be visible the next time the folder is mounted. You can change permissions while in nautilus as root (with the above command) by right clicking on the folder, selecting Properties, then Permissions. Or you can use the 'chown' command from a terminal. Just be careful that if you do a universal chown that it is of the data file and not your system folders.

If you need help with the commands and it is a permission problem, we can help if you provide the mount point of your data partition (e.g. /mnt/mydata, /media/mydata, etc).

You are right, it was just permission problem and running 
```

gksu nautilus

```
helped me to change the permissions to that partition inside nautilus, and now I can read and write to that partition.
thanks problem solved.

---

