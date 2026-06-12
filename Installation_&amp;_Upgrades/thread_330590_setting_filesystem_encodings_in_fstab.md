---
title: "setting filesystem encodings in fstab"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by khughitt on 2007-01-03
Hi,

I wanted to setup my fstab file so that my partitions support different encodings. I looked around some and found that the mount command 

```
mount -o iocharset=gb2312,utf8 ...
```

would work for mounting it. I tried to implement it in the fstab however and the OS didn't load, so i reverted back to the old fstab. Anyone know how to specify multiple encodings in fstab files?

Any help is greatly appreciated- Thanks!

---

### Post by khughitt on 2007-01-11
Okay, i did a little more research a found out how to set-up mounted ntfs / fat partitions to use different encodings, but i'm still having trouble with with encodings on my ext3 partition- some of the folders and filenames show up as strings of questions marks...

anyone have any ideas?

---

