---
title: "Problem with booting"
date: 2023-11-08
forum: Installation &amp; Upgrades
---

### Post by hx-radek on 2023-11-08
One day while boot i got this:
initramfs: Waiting for /dev/mapper/ubuntu--vg-ubuntu--lv to appear
initramfs: Timeout while waiting for devices for / (and possibly /usr) filesystems to appear (did you specified correct ones) initramfs: Will cause kernel panic in 10s...

I chrooted into /dev/mapper/ubuntu--vg-ubuntu--lv and see my files.
i tried update initramfs but it showed none kernels (but before error i can choose 2 version of kernel, both not working).

---

### Post by yancek on 2023-11-08
Were any changes to the system made just prior to this error?  If so, what were they?  Posting the output of the blkid command and the contents of the /etc/fstab file might help someone to help you.

---

