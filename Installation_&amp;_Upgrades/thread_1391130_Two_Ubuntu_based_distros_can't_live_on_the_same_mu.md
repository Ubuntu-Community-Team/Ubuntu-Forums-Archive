---
title: "Two Ubuntu based distros can't live on the same multiboot USB drive."
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by Charrit on 2010-01-26
I made a multi-boot USB pendrive with several live distributions, and I found a problem with using two distros based on "casper":

BT4 doesn't load properly, I supose that BT4 is mounting the squashfs from the Ubuntu distribution during the booting process. I think this because when BT4 finishes the boot process, it shows the motd for Ubuntu 9.10, also, during the booting process it hits some errors of missing libraries and it doesn't make the autologin...

_Tech data:_

*sda ***MBR **has Grub installed and chainloads other systems for preserving distro menus
*sda2 *has** Ubuntu 9.10** Live with Syslinux installed in the partition
*sda3 *has **Back Track 4** Final with Grub installed in the partition

I found a partial fix for the problem, if I rename the "*casper*" directory of the Ubuntu (sda2) to "*casper_disabled*", then I'm able to boot BT4 with no problem.

Any idea to avoid that problem?

Why Casper doesn't use the root partition for booting?
I think that it is using always the first partition containing the casper directory...

Is there a way to rename the casper directory for one of the distros?

Thanks!

---

