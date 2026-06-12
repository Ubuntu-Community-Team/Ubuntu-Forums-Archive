---
title: "All of a sudden GRUB won't install with a new installation"
date: 2015-01-31
forum: Installation &amp; Upgrades
---

### Post by stevenm-wills on 2015-01-31
This is the strangest thing. Usually I install Ubuntu Server with no problems. Today I went to reonstall it on my personal dev server and every time it won't install GRUB. It just says it can"t.

I've looked into solutions, but I want to know why this is happening. My hardware is the same. Im using the same version of Ubuntu. So why all of a sudden does it have an issue with installing GRUB.

Im way behind on a project over this.. Why is this hapening all of a sudden? What changed?

---

### Post by grahammechanical on 2015-01-31
Are you still installing on an Ext4 file system? Or are you installing on another files system? With btrfs we do get an unable to install Grub error unless we have about 1Mib of unallocated space at the beginning of the hard disk.

We can only guess what has changed.

Regards

---

