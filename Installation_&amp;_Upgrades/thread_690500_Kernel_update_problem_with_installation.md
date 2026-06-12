---
title: "Kernel update problem with installation"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by joel@parke.ods.org on 2008-02-07
Hi all,

Every time the kernel is upgraded, the installation scrip sets the wrong hardware for the kernel in grub.  This has been happening for a long time and I am guessing that there is something I can change to resolve this issue.  Any help would be greatly appreciated.

In the most recent event, grup/menu.lst had 

BEFORE:
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/hda2 ro quiet splash
initrd          /initrd.img-2.6.22-14-generic

AFTER:
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/sda1 ro quiet splash
initrd          /initrd.img-2.6.22-14-generic


SO what is causing root to be set to /dev/sda1?????

Please help!  I am sick and tired of fixing this by hand!

Thanks,
Joel Parke

---

### Post by Pumalite on 2008-02-07
If you are able to boot to your system, don't worry. Since Feisty that the kernel sets hda1 as sda1.

---

### Post by torgrot on 2008-02-07
> **Pumalite said:**
> If you are able to boot to your system, don't worry. Since Feisty that the kernel sets hda1 as sda1.

Yes but it is changing the partition too.

torgrot

---

### Post by Pumalite on 2008-02-07
Good catch. I believe that can be avoided by changing 'kopt' and 'groot' in menu.lst permanently.

---

