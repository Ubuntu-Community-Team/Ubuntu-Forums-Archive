---
title: "Debootstrap Feisty Configuration fails"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by devnu11 on 2007-06-30
I am attempting to bootstrap a feisty install as I have previously done.  Today I received an error as follows:

> I: Installing core packages...
W: Failure trying to run: chroot /media/disk dpkg --force-depends --install var/cache/apt/archives/libc6_2.5-0ubuntu14_i386.deb
I have tried the main ubuntu archive and the us archive with the same result.  Any idea why this is happening?

---

### Post by JonathanRRogers on 2007-09-08
I was just trying to set up pbuilder, which uses chroot. I was getting a very similar error to yours. After much frustration, I ran some of the commands manually, which showed me error messages I had previously missed. The errors were about /dev/null. I realized that I had my /var fileystem mounted with the nodev option because I hadn't anticipated needing any device nodes under /var and thought it might improve security. I simply remounted /var without nodev and it all seems to be working now. My filesystem setup was not even close to a default Ubuntu install, so if you haven't tweaked settings in fstab yourself, your problem is probably different.

---

### Post by LucaCappelletti on 2007-10-23
Hi,
remount the fs with:
$sudo mount -o remount,dev /your/fs

If the problem persist try also:
$sudo mount --bind /dev /where/is/chroot/dev

now it should surely go.

Bye,

Luca Cappelletti

---

