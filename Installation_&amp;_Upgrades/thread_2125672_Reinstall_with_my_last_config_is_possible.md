---
title: "Reinstall with my last config is possible?"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by victorsnk on 2013-03-14
HI! What's it going?

Excuse me, I have a question. I have deciding intall Ubuntu Gnome in my computer, but before it I'd like save my "home" configuration. If I do it, I'll start my new OS with my configuration? How can I do this backup? I hope that you can understand me.

Thank you! Bye!

---

### Post by darkod on 2013-03-15
If you want to keep your Home folders during clean installs, it's better to make /home separate partition. Even if it's not separate now, you can create it if you have some unallocated space on the disk. If you disk is fully partitioned (all of it belongs to partitions), you will have to shrink some partition to make space for create the /home partition.

---

### Post by victorsnk on 2013-03-15
Thank you for your answer. Now, I've two partitions: 

1. Ubuntu all system with 30 GB
2. FAT32 partition for to save all documents (videos, photos, music) I did it because I need acces to this disk fron the windows. This partition had 200 GB

Thank you.

Afther that, What is your advice?

---

### Post by darkod on 2013-03-15
How much space you have used in ubuntu? Can you post the output of:
```
df -h
du -sh /home
```

Is Windows on another disk?

You didn't need to create the shared partition as FAT32, ubuntu can work just fine with NTFS.

---

### Post by victorsnk on 2013-03-17
Yes, I have Windows in the other disk. Do you think I could format this disk in FAT32?

---

### Post by darkod on 2013-03-17
You could, but formatting destroys all data. You would need to move the data, format it as NTFS and then move it back.

After that if you are mounting that partition in ubuntu in /etc/fstab by UUID you will have to make adjustments since the UUID will change with formatting.

---

