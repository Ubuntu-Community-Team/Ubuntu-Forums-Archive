---
title: "mdadm problem for someone who has no raid"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by cow_2001 on 2007-04-21
I don't have raid.
While updating Ubuntu to 7.04. I chose, without understanding, "all" instead of "none" in the mdadm dialogue. Now the system won't load.
What should I do to get it working again?

---

### Post by oleoleole on 2007-04-24
> **cow_2001 said:**
> I don't have raid.
While updating Ubuntu to 7.04. I chose, without understanding, "all" instead of "none" in the mdadm dialogue. Now the system won't load.
What should I do to get it working again?

You must boot into your system with a kernel not using mdadm, or else you can use the Live-CD and mount your harddrive and replace the backups of initrd-files with the existing ones.

Ex. /boot/initrd.img-2.6.20-15-generic.bak to /boot/initrd.img-2.6.20-15-generic

You can also check if you have the old kernel in the GRUB list and check if that works first.

After and IF you could login to your computer, just remove mdadm:
Open terminal and write and hit enter:
```
sudo aptitude remove mdadm
```

---

