---
title: "Lockup on Mount of luks Crypt fs at boot"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by ryan8403 on 2010-08-10
It seems I've run into a bit of a problem. I recently upgraded to the latest kernel 2.6.32-24-generic (x86) but when I reboot into the new kernel and type in my password the system hangs, same when using a keyfile on the root file system.

to give an outline of how the disks are setup.

3 hard drives

sda1 / = unencrypted
sdb1 /home = encrypted w/ luks
sdc1 /backup = encrypted w/ luks

When i boot to the original kernel 2.6.32-21 I'm able to successfully get into the system. 

Any suggestions of where to look or what to look for?

Thanks for any help.

---

### Post by ryan8403 on 2010-08-14
bump

---

