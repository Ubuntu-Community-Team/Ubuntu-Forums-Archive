---
title: "How can I tri-boot my laptop with ubuntu"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by yinglcs2 on 2007-05-09
Hi,

I  already have 2 OS (dual -boot) in my laptop: Windows XP and Fedora 5.
How can I  add 1 more OS to tri-boot with Ubuntu?

Thank you.

---

### Post by hal8000 on 2007-05-09
First make sure you have some free space in the extended partion, shrink your last partition with gparted or windows acronis, or whatever you prefer.

Once you have free space, install Ubuntu, the partitioner gparted will install in the free space, make sure you tell it to!! Once installed if you use ubuntu grub, it should add your other OS's.
The alternative is not to install grub, then manually edit your existing grub/menu.lst file and add ubuntu to it.
HTH

---

### Post by yinglcs2 on 2007-05-12
Thanks. I did that. But after I install ubuntu, it can only boot either ubuntu and windows xp, but the boot screen does not let me pick fedora 5  (the linux partition that I have before I install ubuntu).

---

