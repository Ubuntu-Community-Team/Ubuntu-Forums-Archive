---
title: "Crash upgrading from Dapper to Edgy"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by atatistcheff on 2007-10-07
Hi,

I just attempted an upgrade from Dapper to Edgy using: gksu "update-manager -c"

The install and download of new files got to where it had about 9 minutes left and then something crashed.  I'm not real sure what crashed but there was a bugreport file created.  It says the backtrace was generated from '/usr/libexec/gnome-netstatus'

The bottom line is that now the system won't boot.  It starts to but as soon as it tries to mount the filesystem it simply hangs.  I've tried recovery mode and the previous kernel and that kernel's recovery mode too.  Nothing works.  The installation is on a Dell laptop which also has XP so I can use Explore2fs to look at the files on my Linux partition.  

I guess I'd just like to know if there's some way I could possibly recover this system before I have to reinstall the whole thing.  Dapper was working just fine so I'm kicking myself for even trying the upgrade but I guess that's water under the bridge now.  Any help/advice would be appreciated.

Thanks!

---

