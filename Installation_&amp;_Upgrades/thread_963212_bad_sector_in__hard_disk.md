---
title: "bad sector in  hard disk"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2008-10-30
Hi all,

what is the command/method/procedure to check/identify  bad sector in  hard disk ?

---

### Post by cariboo on 2008-10-30
Boot up with the LiveCD and run fsck  in a terminal:

```
sudo fsck -a /dev/sdxx
```

Where /dev/sdxx is you hard drive and partition.

Jim

---

