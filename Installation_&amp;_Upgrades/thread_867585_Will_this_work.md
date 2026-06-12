---
title: "Will this work?"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by mdsharp24 on 2008-07-23
First, let me say I've looked into partimage, g4l, mondorescue, and some others and am quite aware that they exist and work. However, I wanted to get some opinions if this would work just as well...

I have a laptop with Ubuntu installed. My HDD is /dev/sda1

If I boot into a Ubuntu LiveCD and mount a USB external drive (ext3fs) as /dev/sdb1 mounted at /media/disk and run:

dd if=/dev/sda1 | gzip -9>/media/disk/backup.gz

will it create an EXACT clone of the /dev/sda1 partition?

Further, if I'm playing around with my system, and TOTALLY make it unbootable or what not, can I then restore by booting into the LiveCD, mounting the USB external and running:

gunzip /media/disk/backup.gz | dd of=/dev/sda1

Thanks for your thoughts and further suggestions

---

