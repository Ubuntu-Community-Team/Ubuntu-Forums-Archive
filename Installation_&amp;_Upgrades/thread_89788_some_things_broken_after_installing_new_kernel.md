---
title: "some things broken after installing new kernel"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by beijingjj on 2005-11-13
I installed a stock kernel from kernel.org, I used a working .config file that I saved from when I was running Mepis.  I used make-kpgk to make .debs and install them.

Most things seem to load OK but I get the broken HAL message that others have complained about when I log in.  Although it successfully loads the module for my wireless card the card is not known to the operating system when I run ifconfig or iwconfig.  My sound is also broken though the module has been compiled with the kernel.  I wonder if this has to do with HAL being broken.

I looked through /var/log/messages and dmesg and nothing jumped out at me.  Any idea what I can do to troubleshoot this?  I tried running /usr/sbin/hald --daemon=no --verbose=yes but got no useful output to suggest where the problem lies.

Thanks.

---

