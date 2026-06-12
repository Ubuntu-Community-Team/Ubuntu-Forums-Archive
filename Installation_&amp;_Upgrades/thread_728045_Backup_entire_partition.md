---
title: "Backup entire partition"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by stchman on 2008-03-18
I am building a new PC and want to make a backup of my storage partition.  I have an external hdd.  The source is /media/storage and the destination is /media/disk

If I issue the following command:

```
tar -cvzf /media/disk/storage_backup.tar.gz /media/storage
```

Will this get every file hidden or not?

My intent is to create a file called backup on the removable hdd so I can get everything.  I also want to backup my /home folder so should I use the same command:

```
tar -cvzf /media/disk/home_backup.tar.gz ~/
```

Let me know what you think.

---

### Post by Tews on 2008-03-18
The best solution for backing up any linux system is Quick-Start ... See the forum thread here ..

[http://ubuntuforums.org/showthread.php?p=3774207#post3774207](http://ubuntuforums.org/showthread.php?p=3774207#post3774207)

---

