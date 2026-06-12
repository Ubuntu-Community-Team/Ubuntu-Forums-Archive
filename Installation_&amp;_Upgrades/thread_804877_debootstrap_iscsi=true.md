---
title: "debootstrap iscsi=true"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by krdoor on 2008-05-23
I'm trying to debootstrap a ubuntu 8.04 to use as iscsi boot for a thinclient. (via gPXE)

In the release notes I read that iscsi is supported in kernel if you pass iscsi=true during begin of installation.

Since I'm going to debootstrap the system I do not know how or when to pass this option.

I'm following this doc: [https://help.ubuntu.com/community/DebootstrapChroot?highlight=%28debootstrap%29](https://help.ubuntu.com/community/DebootstrapChroot?highlight=%28debootstrap%29)

But when I do:

root@thinclient1:~# /usr/sbin/debootstrap --iscsi=true --arch i386 hardy /mnt/ubuntu8/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
E: unrecognized or invalid option --iscsi=true

Can somebody tell me how to enable iscsi support in kernel when using debootstrap as install method.
Thanks in advance.

K

---

