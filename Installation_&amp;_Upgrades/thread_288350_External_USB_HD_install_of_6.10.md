---
title: "External USB HD install of 6.10"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by fishbolt on 2006-10-29
Hello, forum people!

I'm attempting my second external bootable USB install of 6.10. My first one exposed a number of bugs in the install process (listed at the end) but I feel like I know what I'm doing at this point.

My second install on a different computer hasn't gone so well. I'm able to partition and install ubuntu on the drive. I do the mkinittmpfs with the full set of USB modules, like I did on the other install. I edit grub's menu.lst to refer to hd0,0 since my root is the 1st primary and there are no other filesystem partitions (I do have a swap part of course).

When I boo the drive, grub gives me an "Error 2" and hangs. I've tried various hd #s and checked the path to the image. These all seem ok. Any idea what I've screwed up?

Bugs found in 6.10 x86 desktop install:

 * xorg.conf lists largest monitor size as "1680x1680". There is no such size, of course, so large analog montitors fail unless you edit the xorg.conf on a text console first.

 * gparted conflicts with Ubuntu being a live CD. Once gparted creates one partition, the OS immediately mounts it making any subsequent actions gparted needs to take fail. This is fixable by either using fdisk/mkfs (text) or by turing off automount of volumes (gui).

---

