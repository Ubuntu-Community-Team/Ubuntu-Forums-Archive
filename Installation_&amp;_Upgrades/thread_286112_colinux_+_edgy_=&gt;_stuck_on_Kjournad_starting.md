---
title: "colinux + edgy =&gt; stuck on Kjournad starting"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by motscousus on 2006-10-27
hi,

i had a running config with 6.06 runing fine both booted in colinux or standalone. everything was perfect in a prefect world.

The other day i upgraded to 6.10, recolinuxized the bootup script that where changed during upgrade.( trick described there: [http://ubuntuforums.org/showthread.php?t=81444](http://ubuntuforums.org/showthread.php?t=81444) [http://wiki.colinux.org/wiki/Dual_boot_system](http://wiki.colinux.org/wiki/Dual_boot_system) )

But since then when i start colinux, it hangs (not crashing though) during boot process, the last line in colinux console is: 
"kjournald starting. Commit interval 5 Seconds"

could it have some thing to do with the replacement of init by upstart ? ([https://wiki.ubuntu.com/ReplacementInit](https://wiki.ubuntu.com/ReplacementInit) )

thanks for your help !

---

### Post by motscousus on 2006-10-31
works after installing a dev snapshot  of colinux.
[http://www.colinux.org/snapshots/](http://www.colinux.org/snapshots/)
[http://www.colinux.org/snapshots/devel-coLinux-20061003.exe](http://www.colinux.org/snapshots/devel-coLinux-20061003.exe)

---

