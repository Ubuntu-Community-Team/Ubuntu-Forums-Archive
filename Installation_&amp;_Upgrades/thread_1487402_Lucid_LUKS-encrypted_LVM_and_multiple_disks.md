---
title: "Lucid LUKS-encrypted LVM and multiple disks"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by Blueshell on 2010-05-18
Is using LUKS-encrypted LVMs in Lucid with multiple disks well-supported?  Has anyone tried it?

Specifically:  I have a test machine I just installed Lucid on, using the AMD64-alternate ISO, and used the installer's LVM+encryption setup.  I was surprised to see that the installer encrypts the -disk- and then layers LVM on top of it, instead of setting up LVM and then encrypting the contents of the VG.

If I add a second PV at some point in the future and extend my existing encrypted VG across it, is initrd smart enough to unlock -all- disks with the same passphrase and then attempt to bring up the VG?  I note [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/490917](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/490917), which seems to indicate that Karmic may not be smart enough, but I can't find any information about Lucid.

If this -is- supported, what's the best way to initialize that second disk?

My alternative, of course, is to start over, probably by making an -un- encrypted /boot, having that bring up LVM (perhaps with my own scripts in the initramfs, which I'm trying to avoid), and then do the luksOpen once the VG has been assembled from however many PVs there are.  And -then- the boot can continue.  I'd rather avoid having to do all that work.  (I'd also rather avoid having to figure out how to init a second disk and try to add it to the existing VG just to see if Lucid falls over; I'm hoping for a success story or a pointer to same, or a pointer to a failure or bug report of same.)

Thanks!

---

