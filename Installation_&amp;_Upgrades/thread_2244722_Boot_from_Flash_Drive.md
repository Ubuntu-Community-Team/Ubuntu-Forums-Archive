---
title: "Boot from Flash Drive"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by Gunzoid on 2014-09-18
I can't find the correct answer to this.
I have a bootable DVD.
Can those files just be copied to a flash drive so it's bootable?
(not an .iso file)

---

### Post by oldfred on 2014-09-18
You definitely cannot copy with standard copy commands.

If you have an ISO you can use dd to copy the ISO to a flash drive which does not create a standard partitioned flash drive but one that is like the DVD image. And then you have to use dd to erase the boot sector so you can use flash drive, so I generally do not suggest dd. And dd needs same size to same size or smaller. 

You may be able to copy files then install syslinux separately (or grub).

Just a lot easier to use ISO and standard install tools.

---

