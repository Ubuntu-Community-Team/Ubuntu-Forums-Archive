---
title: "LVM2 vs bind-style mount, SSD+HDD?"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2013-05-08
Planning an installation starting with Server, and I wonder about not using LVM2 in favor of a bind-style directory mount.

I have an SSD and some HDDs.  In the past I've been making logical volumes and growing or shrinking them accordingly in LVM2.  I wonder if I'm making more work for myself for no purpose.

so what I was thinking is this:
SSD:  1 partition:
/
/ssdmounts (directory containing SSD directories mounted from an HDD mount point)

HDD: 2 partitions:
swap
hddmounts (contains HDD directories mounted from an SSD partition)

The box will mostly be my personal workstation.  I'm a software developer, so it will see lots of compiling and testing, and I need to have a few VMs (thinking KVM here) a couple of which will run mostly continuously and others which run occasionally for testing purposes.

Thanks.

---

