---
title: "cant find windows files when its in sleep state"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by mkrahmeh on 2008-04-28
Dear all
i have both windows vista and kubuntu installed on my machine..
but i've noticed that when leaving the windows in the sleep state and booting the linux, the latter cannot find any files in the windows' partition, i tried using the konsole and the dolphin as well, but the C seemed to be empty
after restarting the machine and shutting down the windows the files appeared again in linux..can any one explain this anomaly..?? 

thx
mohammed abu rahmeh :popcorn:

---

### Post by damis648 on 2008-04-28
This is because when windows is hibernating / sleeping, the NTFS filesystem is changed to the hibernation state and cannot be mounted properly... If you want to force mount it you can try that however it may damage the filesystem.

Try force mounting with:

```
mount -t ntfs-3g /dev/xxx /media/disk -o force
```

and replace xxx with the drive listing (ie hda1 hda2 etc..)
and if you want to replace "disk" with another mount folder name you can

---

