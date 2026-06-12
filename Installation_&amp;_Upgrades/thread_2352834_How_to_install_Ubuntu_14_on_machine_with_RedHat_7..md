---
title: "How to install Ubuntu 14 on machine with RedHat 7.2 as dual boot"
date: 2017-02-16
forum: Installation &amp; Upgrades
---

### Post by sharonapa on 2017-02-16
Hi,
Is there a simple and safe manual on how to install Ubuntu 14 on machine with RedHat 7.2 as **dual boot**?
thanks in advance on your help.

---

### Post by oldfred on 2017-02-16
I believe Redhat normally uses LVM. Is that how you have installed?

If so probably better to install to another logical volume. Ubuntu normal install is just to a partition. And its default LVM install erases entire drive.
You still should be able to use Something Else, but I do not know LVM.

Post this:
sudo parted -l

---

