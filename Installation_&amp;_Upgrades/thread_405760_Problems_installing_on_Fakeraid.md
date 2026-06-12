---
title: "Problems installing on Fakeraid"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by zeroflag on 2007-04-10
Hello everyone,

I'm having some issues installing ubuntu (7.04 beta) on my 2x74GB (fake)raid0.

I tried installing from the alternate cd but it only offers me to install on one of the hdds, not on both/raid.

I tried the live-CD but the installer only recognized the physical disks and even when I installed dmraid and created all partitions prior to installation, it would fail at some point.

I also tried the [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") which allowed me to get a basic system on my fakeraid but then wouldn't let me boot it - as in [bug 83231]("https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/83231").
Furthermore I tried ALL of the suggested workarrounds from the bug but none worked.
Still getting "no block devices found" after I select the target from grub - and I remember that line from dmraid... just can't remember how I fixed it or why I'm getting it again.

consequentely, I am stuck.
I don't have any other hdd to install ubuntu on (I could spare a few mb for a boot partition but not more) and I can't/don't want to destroy my windows installation which is on the same fakeraid (already resized that so I have 52GB for ubuntu).

Any suggestions what I could try?

so long.

PS: can't even try edgy live because x refuses to start. (probably outdated graphics driver)
PPS: there is/was an error when I installed dmraid on the bootstrap system. I had to remove "set -e" from dmraid's init.d file.

Hardware:
Asus M2N-SLI Deluxe (nforce 570 AMD)
AMD Athlon 64 3600+ X2
2x1GB DDR2 PC800 Corsair
2xWDC WD740GD as raid0 (partition 1 is 2GB swap, 2 is 50GB reiserfs, 3 is NTFS windows)
Gainward Bliss 8800GTS GS

---

### Post by zeroflag on 2007-04-10
the fakeraidhowto got the system working now. there seems to be an issue with chroot because if you don't leave it (ctrl D), remount everything and chroot back into the target, it won't work.

---

