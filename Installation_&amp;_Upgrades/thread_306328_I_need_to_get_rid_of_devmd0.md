---
title: "I need to get rid of /dev/md0"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by CameronCalver on 2006-11-24
Hello i have a few tryes at setting up ubuntu with raid and i could not get it to work but i finaly got it.
So i installed ubuntu on the /dev/sda drive and it worked i restared it and it would not boot becuase a couple of weeks ago i was fiddeling around with mdadm and i created a /dev/md0 drive so when it boots it mounts /dev/md0 then it tryes to mount /dev/sda and becuase that is already mounted it will not mount
Is there someway i can delete the fake raid arrays i created with mdadm

---

### Post by jayDubb on 2006-12-11
Anyone resolve this? I've got the exact same problem. I can ```
mdadm --stop /dev/md0
```, then ```
mount -a
``` my ntfs(fuse-ntfs3g)..but I cant stop /dev/md0 from starting up! I've tried changing the rc files, and even removing lvm/mdadm packages...to no avail? Ideas/clues?

---

