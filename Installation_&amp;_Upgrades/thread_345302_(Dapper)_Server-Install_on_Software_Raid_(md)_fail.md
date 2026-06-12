---
title: "(Dapper) Server-Install on Software Raid (md) fails"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by nanocosm on 2007-01-24
Hi everyone!

I've trouble installing a server using the alternate install cd.
I want to install a system on a software raid (md, no fakeraid, no lvm), following the wiki guide but after final reboot I get these error.

```

eval: 1: 8: not found
mknod: sdb: File exists
eval: 1: Syntax error: ";" unexpected
mdadm: error opening /dev/md?: No such file or directory
mdadm: error opening /dev/md?: No such file or directory
mdadm: error opening /dev/md?: No such file or directory
mdadm: error opening /dev/md?: No such file or directory
mdadm: error opening /dev/md?: No such file or directory
mdadm: error opening /dev/md?: No such file or directory
Done.
Begin: Waiting for root file system... ...
Done.
ALERT! /dev/md2 does not exists. Dropping to a shell!

```

This is my partition scheme:

/dev/sda1 & /dev/sdb1 --> /dev/md0  /boot
/dev/sda2 & /dev/sdb2 --> /dev/md1 swap
/dev/sda3 & /dev/sdb3 --> /dev/md2 /   (root)


Why ubuntu can't be run from a sw-raid? This install needs to be fail-save, not the fastest.

Any ideas anyone, please?

---

### Post by nanocosm on 2007-01-25
Does really no one has the same issue out there ?

---

### Post by loewi on 2007-02-05
[https://launchpad.net/distros/ubuntu/+source/mdadm/+bug/57972](https://launchpad.net/distros/ubuntu/+source/mdadm/+bug/57972)

---

