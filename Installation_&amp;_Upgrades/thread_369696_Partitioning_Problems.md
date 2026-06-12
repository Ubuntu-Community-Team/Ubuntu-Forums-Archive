---
title: "Partitioning Problems"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by fmkguy on 2007-02-24
Okay, I'm really new to all of this...

I've partitioned my HD into four parts: 1 for my Windows XP boot, 1 for the Ubutnu boot, 1 for files, and the last one for the linux swap. All but the swap partition are ntfs (?). When I go to mount the partitions, I set one at "/", one at "swap", and then just leave the other two at their defaults.

(BTW, this is for a dual-boot system)

When I click next, however, it says that I don't have one placed at "/". Is that because it shouldn't be set at ntfs? Should I have set it as fat32 or one of the other options?

Thanks in advance for any help you guys could offer.

In HIM,
Joseph<><

---

### Post by foxmulder881 on 2007-02-24
The Ubuntu partition should be set to ext3 and not NTFS. Also, your files partition, is that for Windows files or Ubuntu files?

---

### Post by fmkguy on 2007-02-24
If possible, both...but I guess it's for Windows mostly.

---

### Post by foxmulder881 on 2007-02-24
You could use it for both if you use NTFS. However, mounting NTFS in Ubuntu is a little bit dodgy from what I've heard. I've never done it myself so I couldn't tell you how to. But I have no doubts that there's a tutorial on the forums here somewhere. Have a look around. But personally, I wouldn't recommend it.

---

### Post by fmkguy on 2007-02-24
Thanks. This'll really help!!!!! ;D

In HIM,
Joseph<><

---

### Post by foxmulder881 on 2007-02-24
> **fmkguy said:**
> Thanks.

No probs. ;)

---

