---
title: "libuuid.so.1 issues after upgrade to 11.10"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by EnkiduinNZ on 2011-11-13
Ubuntu 64 bit, Grub, not Grub2.

I upgraded from 11.04 to 11.10 with a number of issues. The one I am pursuing here is a problem with UUIDs at boot.At first I could not boot at all, but I fixed that by replacing the UUID on the root ('/') with the path (/dev/sda8). (Note: I'm using Grub, not Grub2). On boot I still get a message "blkid: Error while loading shared libraries ... libuuid.so.1 No such file or directory". The message is for another mount ('/ext2'), not root ('/'). 

After boot the 'blkid' gives the correct results, even the correct UUID for the root device, so it seems that the issue only happens at boot time. Also the mounts for which I get the messages **are** in fact mounted!

```

root@bumblebee:~# blkid
/dev/sda1: UUID="009048F69048F3A6" TYPE="ntfs" 
/dev/sda5: LABEL="SHARE" UUID="B0AF-3526" TYPE="vfat" 
/dev/sda6: LABEL="New Volume" UUID="2EEC0C87EC0C4C11" TYPE="ntfs" 
/dev/sda7: UUID="ad9de9fa-fcdb-400f-813c-ff232dc6f38d" TYPE="swap" 
/dev/sda8: UUID="9113cc9a-5e89-4387-9b89-1a31e9e1b2c5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="334ba25c-320f-4dd5-9174-db7ef1289463" TYPE="ext3" 

```

libuuid.so.1 **does** exist on my system, as a link from /lib32/libuuid.so.1 to /lib32/libuuid.so.1.3.0

Does anyone have any ideas?

Cheers,

Cliff

---

### Post by EnkiduinNZ on 2011-11-26
Any ideas anyone? I've talked to others who have this issue and they haven't got any solutions.

Cheers,

Cliff

---

