---
title: "Two disks dm-crypt setup"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by dk_zero-cool on 2012-07-14
Hi.
At the moment I am running Ubuntu with an lvm2,luks dm-crypt setup. My layout looks like this:
```
/dev/sda1				ext2			/boot
/dev/sda2				luks			none
/dev/sda3				extended
-> /dev/sda5				lvm2/luks
-> -> (lv) root				xfs			/
-> -> (lv) home				xfs			/home
-> -> (lv) storage			xfs			/media/storage
-> -> (lv) additional			xfs			/media/additional
-> -> (lv) swap				swap
```

Now I am thinking of buying an SSD disk to run my system on (Boot, Root, Home and Swap), while keeping the rest on the old drive. However I would still like to have both the SSD Encryptions and the old HDD Encryptions be unlocked during boot, but without typing the password twice.

---

