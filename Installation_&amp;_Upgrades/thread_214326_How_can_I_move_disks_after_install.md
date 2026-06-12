---
title: "How can I move disks after install?"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by lmunro on 2006-07-12
I currently have a home web and file server (on FreeBSD) on one machine which I want to replace with Ubuntu (on the same machine, because I'm tired of compiling ports on a k6-2...)
I want to avoid downtime as much as possible so I want to install Ubuntu on my desktop machine (the server version) on two new drives as a RAID1 using LVM and then switch the drives from one machine to the other after configuring the services and rsync'ing the relevant data.
Will it boot? I assume I'll have to edit some of the configuration, such as eth0 and /etc/fstab but I'm worried about grub and perhaps the LVM. The disks will be changing from hde and hdf to hda and hdb. Can I use the install cd to reconfigure grub so that the system boots after which I'll be able to change the necessary config files?
Any thoughts on what pitfalls I should look out for, or obvious things I might have overlooked?
Any help is much appreciated...

---

### Post by aysiu on 2006-07-12
[http://www.codeweavers.com/support/docs/crossover-pro/install](http://www.codeweavers.com/support/docs/crossover-pro/install)
may help for Crossover Office

[http://www.ubuntuforums.org/showpost.php?p=1138374&postcount=24](http://www.ubuntuforums.org/showpost.php?p=1138374&postcount=24)
may help for Google Earth

---

### Post by lmunro on 2006-07-12
Aysiu,
Are you sure this is relevant to this thread?

---

### Post by aysiu on 2006-07-12
> **lmunro said:**
> Aysiu,
Are you sure this is relevant to this thread?
Oh... I guess I must have accidentally posted to the wrong thread! Sorry for the confusion.

---

