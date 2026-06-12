---
title: "Feisty: Volume group &quot;Ubuntu&quot; not found, can't boot"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by augustojd on 2007-01-02
Hello all,

I've just updated my Feisty installation after being on holidays since Dec 23rd. When I rebooted the computer with the latest kernel (2.6.20-2-386), I got the following messages:

Loading, please wait...
mdadm: No devices listed in conf file were found.
   Volume group "Ubuntu" not found
      Check root= bootarg cat /proc/cmdline
      or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/mapper/Ubuntu-root does not exist. Dropping to a shell!

And then I get the BusyBox ash prompt.

I can boot a 2.6.19 kernel, but the nvidia driver has already been updated to the latest kernel.

Any ideas of how to fix this?

Cheers.

---

