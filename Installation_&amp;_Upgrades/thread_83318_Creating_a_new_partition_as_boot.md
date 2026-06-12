---
title: "Creating a new partition as /boot"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by Daedalus on 2005-10-28
Hello,

I have created a new partition with ext3 as the filesystem and I want to adjust my system to run this new partition as /boot. I was thinking of moving all /boot directory contents to this new partition and adding the following line to /etc/fstab: /dev/hda4 /boot defaults 0 2.

Anyone can help me with this?

Thanks!

---

### Post by taurus on 2005-10-28
You can download the LiveCD and boot your machine from it.  Then, mount your partitions and copy /boot/* to your new /boot/.  Also, you need to edit your /etc/fstab to reflect the change to your new /boot...

---

