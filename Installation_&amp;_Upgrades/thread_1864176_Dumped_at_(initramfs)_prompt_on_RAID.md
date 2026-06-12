---
title: "Dumped at (initramfs) prompt on RAID"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by shinyblue on 2011-10-18
Hi lovely community...

I have a machine with software RAID1 set up.

md0 is made up of sda1 and sdb1
md1 is made up of sda2 and sdb2
md2 is made up of sda6 and sdb6

md1 has been / and md2 has been /home/

md0 and md1 are exactly the same size.

I wanted to clone the Ubuntu Natty in md1 into md0 so that I could to a test upgrade to Oneiric, while keeping the original Natty set up in md1. This way I could ensure zero disruption for the other users of the machine while I fought the likely problems and tweaks with the Oneiric.

Well that backfired. Can't boot the machine now!

What I did was (from memory!):
[LIST=1]
[*] created new ext4 fs in the md0 partition (with Gnome Disk Util)
[*] mounted this at /mnt/oneiric
[*] used cp -ax to copy everything from / to /mnt/oneiric taking care to exclude proc, sys, home (that's on md2), dev.
[*] edited /mnt/oneiric/etc/fstab with the new UUID for /
[*] created /etc/grub.d/09_oneiric to add a menu item for the md0 RAID root.
[*] ```
for f in dev proc sys ; do mount --bind /$f /mnt/oneiric/$f; done
```
[*] ```
chroot /mnt/oneiric bash
```
[*] ```
update-initramfs -c -k all
```
[*] Exited the chroot and rebooted
[/LIST]

Now lots has happened since I did this because I've tried and tried different things to get it up again.

Somehow my RAID got degraded. I'm rebuilding it now (from within initramfs), which because it's 500Gb gives me ample time to write this!

So basically: I can boot the kernel, and initrd.img gets unpacked, but then I'm stuck. Must be a problem with init?

I've tried to figure out what the 'init' script does that's inside initrd.img - seems to mount the real root fs at /root/, then ```
mount -o move
``` proc and sys into the real root. Then it somehow (re)mounts / at the propper root and passes over to the real init binary.

I'm hoping if I get it booted then something like update-grub / update-initramfs -u will 'fix' it.

Lost. Can you help?!

---

