---
title: "Fresh 18.10 install wants to remove LVM2"
date: 2018-11-23
forum: Installation &amp; Upgrades
---

### Post by Bedlore on 2018-11-23
Hi all, I've just installed Ubuntu Studio 18.10.  After doing basic apt-get upgrades it installed the latest kernels, but now wants to remove LVM ie.

> The following packages were automatically installed and are no longer required:
  dmeventd libdevmapper-event1.02.1 liblvm2app2.2 liblvm2cmd2.02 libreadline5 lvm2

On an earlier install attempt I think I must of agreed to remove these and then was unable to boot and just got dropped into initramfs, with the "ALERT! /dev/ubuntu-studio-vg/root does not exist. Dropping to a shell!

Can someone tell me if this is what broke my earlier install and if so why it wants to remove it now?

Thanks

---

### Post by Bedlore on 2018-11-25
anyone?

---

### Post by Dennis N on 2018-11-26
> The following packages were automatically installed and are no longer required:
dmeventd libdevmapper-event1.02.1 liblvm2app2.2 liblvm2cmd2.02 libreadline5 lvm2 

"automatically installed" means they were installed as dependencies, but now no package depends on them so apt informs you they could be removed. That doesn't mean it's a good idea. Wisely or not, apt expects the user to decide whether to allow removal of any of these. When I see this, I usually just ignore it. I don't think Ubuntu Software or Gnome Software give this suggestion because it is confusing to users. 

Note: you can prevent a package from being suggested for removal by marking it as "manually installed"

Remove lvm2 from suggestions for auto-removal:
```
sudo apt-mark manual lvm2
```

---

