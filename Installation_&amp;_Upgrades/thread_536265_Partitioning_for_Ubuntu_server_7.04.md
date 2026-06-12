---
title: "Partitioning for Ubuntu server 7.04"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by HellBird on 2007-08-27
Hello,

I have a problem with creating partitions for my Ubuntu server 7.04 box. I have three SATAII disks 250GB each, which I want to connect in RAID 5 array. That sums around 500GB of free size. Now I want to create the following partitions using this RAID array:

&#8226; /boot 128 MB
&#8226; / 30 GB (for root partition)
&#8226; /var (the rest of free space)

Is this even possible to do? I'm completely new to RAID and also Linux so I have no idea if this is even possible.

My server is based on Intel Board S5000PAL (64bit Xeon), which also supports hardware RAID. Please tell me if it would be even better to use hardware RAID and if, where to get driver for Ubuntu Server 7.04 and also how to install the driver before installation, so I can actually make my partitions as I want.

Thank you for helping!

Best wishes!

---

### Post by Divan Santana on 2007-12-10
I would love to know as well.
The CD comes with RedHat and Suse support but no Ubuntu support.

Does that mean I have to use Centos/RedHat for Hardware RAID or be forced to use software RAID on Kubuntu?

That would be unfortunate, sure there must be a way!?

---

