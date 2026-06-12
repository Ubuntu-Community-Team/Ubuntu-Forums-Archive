---
title: "test btrfs compress mount option"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by ZomZilla on 2012-04-01
hi,

i installed ubuntu 11.10 after spending some time with Arch and Gentoo (DIY distro sounds good but theres always something to overlook/forget)

anyways

i have BTRFS / and /home partitions (ext2 /boot) and just added compress=lzo to my fstab to see if there was a noticeable performance gain (after a few updates all the files should have been modified and therefor compressed right?)

so my options look something like this:  defaults,compress=lzo,subvol=@  

is there a way to test if the new mount option has taken effect?
also does anyone know of a trick to get btrfs to compress all my stuff?

thanks in advance

---

