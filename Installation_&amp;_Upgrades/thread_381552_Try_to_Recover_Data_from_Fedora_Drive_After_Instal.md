---
title: "Try to Recover Data from Fedora Drive After Installing Ubuntu.  Help!"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by dealmaker on 2007-03-11
Hi all,
   Long story short, my old laptop which was running Fedora core 6 went dead.  I was able to save the hard drive.  I bought a new laptop, and I installed Ubuntu on it.  Now, I am trying to recover my personal data from the old hard drive which had Fedora installed.  I plugged this hard drive into an usb enclosure, and I plugged it into my new laptop and try to read the data in it in Ubuntu.  But I can only see the "/boot" directory, I can't see any other directories outside "/boot".  Why?  How do I go around that?

Thanks.

---

### Post by taurus on 2007-03-11
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by dealmaker on 2007-03-11
This is the one that is corresponding to the old hard drive:

Disk /dev/sdd: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1          13      104391   83  Linux
/dev/sdd2              14        4864    38965657+  8e  Linux LVM

> **taurus said:**
> What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

