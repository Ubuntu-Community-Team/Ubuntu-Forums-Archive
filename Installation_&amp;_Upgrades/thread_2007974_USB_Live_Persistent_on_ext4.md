---
title: "USB Live Persistent on ext4 ?"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by C.S.Cameron on 2012-06-21
> Originally Posted by C.S.Cameron View Post
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent

> That did not work for me because /cdrom not writable. 

I was referring to persistent install on USB.
To run persistent from Live CD, you need to have a casper-rw file or partition on flash or HDD. 
Press F6 after booting the CD, then type <space>persistent.

```
 persistent
```

---

