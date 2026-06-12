---
title: "Making a Lucid ISO with grub instead of grub2"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by g14n0 on 2010-06-14
Hi, guys.
I need to modify an Ubuntu Lucid ISO to be installed with grub instead of grub2.
I tried to substitute the grub-pc package with grub (grub-legacy) in a chrooted squashfs, and so to remaster the iso and to install it.
But after the installation there is always grub-pc!!!
Any idea?
Thanks a lot

---

### Post by g14n0 on 2010-06-23
Hi, guys.
According to the latest discovers... there's need to modify the ubiquity installer (script grub-installer) to make grub2 discarded and grub installed.
But still doesn't work... Because the installer can't run update-grub to the fresh installed system.

To be continued...  :confused:

---

### Post by darkod on 2010-06-23
It's better to use grub2 than grub1 anyway.

For some specific situation where grub2 can't work for you, when installing ubuntu just select not to install the bootloader by clicking the Advanced button in the last screen.

It will install without a bootloader. Then you would have to use the cd in live mode, chroot into your installation and tell it to install grub1, the packages grub and grub-common.

It should work like that.

But again, if you can use grub2, but are just not familiar with it, don't avoid it because of that. Just learn few basic things and it works fine, in fact much better than grub1.

---

### Post by g14n0 on 2010-06-23
Eureka!

To avoid manual reverting after installation, I've modified the ubiquity
script of grub-installer from chroot in a unsquashed filesystem, and so
I've put the cd together.
Now, it's possible to have a clean installation of lucid with grub1 (aka
grub-legacy).

If interested:  [http://www.mediafire.com/?ic2eyddwz0q](http://www.mediafire.com/?ic2eyddwz0q)

Greetings

---

### Post by dino99 on 2010-06-23
wrong way anyway, as posted into #3, better to learn how to use grub2

---

### Post by g14n0 on 2010-07-08
grub2 has a lot of issue about rt-kernel and rtai.
so the only way to boot a right rtai-patched kernel is to install grub1.

If you need a distro rtai-patched that runs without problems even if you install it, the very only way is to revert grub2 to grub1!

---

