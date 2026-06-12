---
title: "[SOLVED] Can't view files on partitions after upgrade"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by Zyzzyva100 on 2008-06-16
A program I need to use finally become unusable without upgrading, and I couldn't upgrade without upgrading ubuntu, so I went from 6.06 to 7.04 to 7.10 to 8.04 tonight (all server versions).  The stepwise update is what all the posts I found around here seemed to recommend for my specific situation.  The upgrade worked fine, except for the fact that I can no longer see the folders that were on my various partitions prior to the upgrade.

My fstab is the same, and the partitions are still there, they just display as blank.  When I attach the drives to my gentoo box, however, I can see the files just fine.

Unless I am missing something really simple here, I just can't seem to figure out what could be causing this.  Anybody have any ideas as to how I can get my files back?

EDIT:  Actually, upon further inspection, it looks as though maybe the drives just aren't mounted?  I can't seem to mount them though, I get the error: "special device /dev/hdc1 does not exist".  Still no ideas on what could be causing this.

---

### Post by iaculallad on 2008-06-16
Re-place the drive w/c files can't be read, on your upgraded system. Post the result of:

```
sudo fdisk -l
sudo blkid
```

and your fstab file too.

---

### Post by Zyzzyva100 on 2008-06-16
Actually I suppose we can change this to solved now.  Just before you posted I figured I might want to check fdisk, and I noticed that my device names had changed.  I don't know if thats something that occured in the upgrade, or what but my mass storage drive (IDE) went from being hdx to sdx, and so that made my fstab completely wrong.  But now everything is ok again.

---

