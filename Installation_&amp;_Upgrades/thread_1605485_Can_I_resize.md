---
title: "Can I resize"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by Mortesins93 on 2010-10-25
Hello,
This is my partition table:
/dev/sda1               1        4255    34178256   83  Linux
/dev/sda2            4256        4437     1461915    5  Extended
/dev/sda3   *        4438        9964    44395627+   7  HPFS/NTFS
/dev/sda5            4256        4437     1461883+  82  Linux swap / Solaris

I would like to create a new partion to install Ubuntu 10.04 without touching Windows. Can I resize the first partion and create a new one? Should I move the first partition and the extended too? Is it risky? I don't want to do a clean install because I want to keep the Ubuntu which is in the first partion.
Hope you can help me.
Thanks in advance

---

### Post by kansasnoob on 2010-10-25
Please post the full output of:

```
sudo parted /dev/sda print
```

Also placing it in code tags makes it a bit easier to read :)

---

