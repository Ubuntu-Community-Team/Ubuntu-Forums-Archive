---
title: "Installing Crunchbang (currently dual booting Windows 7 and Kubuntu 9.10)"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by punk4rock on 2010-03-15
I am currently dual-booting Windows 7 and Kubuntu 9.10.
Would I be able to delete the partition that Kubuntu is residing in, make a new one and install Crunchbang on that? 
I am wary because I know deleting the partition will eradicate GRUB so I won't be able to access Windows. 
If I insert the Crunchbang Live CD will I be able to install and recover GRUB (and Windows) (if that is the bootloader CB uses?)?

Many thanks in advance.

---

### Post by snowpine on 2010-03-15
CrunchBang 9.04 (the current version) is based on Ubuntu 9.04. It uses the exact same installer. It has the same partitioning options as when you installed Kubuntu 9.10, and it should install GRUB no problem.

The only detail to remember is that 9.04 uses GRUB 1, so it will be a little different than the GRUB 2 you're used to from 9.10. It should detect your Windows the same though. :)

You can refer to the official 9.04 installation instructions and guides in the Ubuntu Wiki if you have any questions, since it is the same installer.

---

### Post by punk4rock on 2010-03-15
> **snowpine said:**
> CrunchBang 9.04 (the current version) is based on Ubuntu 9.04. It uses the exact same installer. It has the same partitioning options as when you installed Kubuntu 9.10, and it should install GRUB no problem.

The only detail to remember is that 9.04 uses GRUB 1, so it will be a little different than the GRUB 2 you're used to from 9.10. It should detect your Windows the same though. :)

You can refer to the official 9.04 installation instructions and guides in the Ubuntu Wiki if you have any questions, since it is the same installer.
Are you saying I should delete Kubuntu totally or just install over it?
Thanks

---

### Post by km0r3 on 2010-03-15
> **punk4rock said:**
> Would I be able to delete the partition that Kubuntu is residing in, make a new one and install Crunchbang on that? 
That's perfectly possible.

---

### Post by snowpine on 2010-03-15
> **punk4rock said:**
> Are you saying I should delete Kubuntu totally or just install over it?
Thanks

No difference. "Installing over" Kubuntu will have the effect of "deleting" it.

---

### Post by punk4rock on 2010-03-16
> **snowpine said:**
> No difference. "Installing over" Kubuntu will have the effect of "deleting" it.
*facepalm* Of course, it was late, d'oh! 
Thank you both for your help.

---

