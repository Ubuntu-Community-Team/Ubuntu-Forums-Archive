---
title: "server upgrade stays at 2.6.32-27"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by dgermann on 2011-03-22
Hi--

Tonight I dist-upgraded a server and it downloaded and installed 2.6.32-30-generic-pae. But when I uname -a, it shows 
```
Linux bak 2.6.32-27-generic-pae #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux
```

It may be because I said keep the old grub menu.lst in answer to its one question. I tried running /sbin/update-grub, but the menu.lst still only shows the -27 kernel.

Is this what it should show, or should I run something else to update the grub menu.lst so it runs the latest kernel?

This is a headless machine accessed only through ssh, and only has cli.

Thanks!

---

