---
title: "Cloning to different hardware with rsync?  Boot problems."
date: 2012-08-06
forum: Installation &amp; Upgrades
---

### Post by ubonetu on 2012-08-06
Hello,

I'm working on two Ubuntu 11.10 boxes and I'm trying to rsync over the entire server (#1) to a different machine (#2) and wish to somehow reinstall just the core system on the second machine, keeping all the other files and booting in case of a failure on system #1.

I've been struggling trying to boot #2 from a straight rsync clone but know I'm missing a major step.

It seems I saw a way to do a core system install, leaving the other files with the Alternate cd but I can't seem to find it again.

Any help appreciated,

wb

---

### Post by darkod on 2012-08-06
The partition(s) on the second machine will not have the same UUID as on the first one. So you will need to check the UUIDs with:
```
sudo blkid
```open /etc/fstab on the second machine and replace the old UUIDs with the new ones.

You will probablt need to reinstall grub2 on the MBR since during that process it connects to the config files on the partition.

If /dev/sda1 is your root and you don't have a separate /boot partition, from live mode it would be something like:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That should get a cloned system up and running.

---

