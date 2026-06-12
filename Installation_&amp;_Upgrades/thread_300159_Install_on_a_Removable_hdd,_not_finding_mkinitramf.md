---
title: "Install on a Removable hdd, not finding mkinitramfs"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by dracule on 2006-11-15
I am trying to install edgy on a removable hdd but am having trouble:

I am following a guide posted but
I am guessing when the guide says Rescue mode it means "repair a broken system"
I then mounted the correct partition (in my case /dev/sdb1 (the same one that i wrote the mbr to, which was 300gb)
But when i hit Ctrl-Alt-F2, and typed in the following:
mount -tproc proc /target/proc
chroot /target
su

all goes well

but when i type this in:

nano /etc/mkinitramfs/modules

it doesnt find the file... it creats a new one.

so how do i do this?

---

