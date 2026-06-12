---
title: "Mount errors at startup"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by SickBoy on 2005-03-04
I had to install windows before I installed Ubuntu and here started all my pain :(

Seems like windows installation changed all partition numbres. I really don't know why because I didn't changed anything about partitions from windows and I have a problem trying to boot Ubuntu again.

I tried editing /etc/fstab and generating a new initrd.img file and still no luck.

Any more ideas?

---

### Post by alastair on 2005-03-04
No idea really - you give no information i.e.

What mount errors at startup?  Check the logs :

/var/log/syslog

What is your partitioning scheme on disk e.g.

sudo fdisk -l /dev/hda

What is your fstab :

cat /etc/fstab

---

