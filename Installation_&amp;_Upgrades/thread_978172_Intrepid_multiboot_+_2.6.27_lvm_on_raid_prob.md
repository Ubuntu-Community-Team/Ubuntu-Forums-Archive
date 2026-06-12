---
title: "Intrepid multiboot + 2.6.27 lvm on raid prob"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by janhurst on 2008-11-10
Hi,

I am trying to bring my ubuntu installs back to life. I updated a 32bit hardy install to intrepid and was bitten by some bugs relating to LVM volumes over RAID. The current 2.6.27 kernel doesn't seem to like this, a previous version of the kernel seemed ok. I then managed to nuke off the previous kernels so I'm stuck unable to boot. I then tried to setup a 64bit intrepid and ran into similar probs.

My system has a RAID1 /dev/md0 for /boot and a RAID0 /dev/md1. Inside /dev/md1 I have a LVM volume group with various volumes, ie a volume for ubuntu32, a volume for ubuntu64, a volume for fedora, a volume for /home etc etc.

Is it possible to share the /boot between ubuntu32 and ubuntu64 installs? If i boot from a live disk and chroot into the installs, and try to apt-get linux-image-generic then the 32bit and 64bit kernels seem to overwrite each other. Does anyone have any suggestions here?

In fact has anyone managed to get LVM on RAID volumes to work with any intrepid 2.6.27 kernel?

cheers

jan

---

