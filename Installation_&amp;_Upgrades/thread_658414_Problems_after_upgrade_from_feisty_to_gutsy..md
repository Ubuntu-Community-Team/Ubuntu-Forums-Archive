---
title: "Problems after upgrade from feisty to gutsy."
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by IBG on 2008-01-04
Hi,
I used to have only gutsy on my laptop then i needed to install windows.
so i formated my harddrive installed vista and then treid to reinstall ubuntu with the live cd.
Booting from the live cd ends up with busy box so i wasn't able to  install gutsy.
I googled around and found out about wubi so i used it to install feisty and then used lvpm to migrate to a normal install.it worked great. Now i  wanted to upgrade to gutsy so i did it with update-manger it  was ok too. 
I reboot the computer and try to boot gutsy kernel and i end up with :
```
Kernel panic -not syncing VFS:Unable to mount root fs on unknown-block(0,0)  
```
 here is my menu.lst [http://rafb.net/p/qy6YLQ21.html](http://rafb.net/p/qy6YLQ21.html)
I still can use the old kernels to boot ubuntu.
Thanks for your help.
I'v also changed root option to /dev/sda2 but it didn't work.

---

