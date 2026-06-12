---
title: "kernel updates to the same version"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by doru001 on 2011-12-18
Some kernel updates for Ubuntu 8.04 lts server do not change the kernel version or the menu.lst entry for the newly installed kernel at all. In /boot only initrd.img-2.6.24-30-generic dates from the last upgrade. initrd.img-2.6.24-30-generic.bak is older. Is this normal?

---

### Post by Frogs Hair on 2011-12-18
I don't know if it is normal , but I remember at least one kernel update like this . The kernel version stayed the same but there was some sort of update . Viewing a change log for the kernel would be the only way to find out what was changed .

---

### Post by MAFoElffen on 2011-12-18
> **doru001 said:**
> Some kernel updates for Ubuntu 8.04 lts server do not change the kernel version or the menu.lst entry for the newly installed kernel at all. In /boot only initrd.img-2.6.24-30-generic dates from the last upgrade. initrd.img-2.6.24-30-generic.bak is older. Is this normal?
Yes, that is normal and is a good thing to make a backup of what was current. If there was any changes in udev or modprobe.d, it would update the ram disk image to incorporate those changes... meaning you didn't necessarily get any kernel changes for that to occur. 

My Personal Own Curiousity = I used that version server edition when it was released. That server version was current, what, 4 years ago?  8.04 hasn't been supported in a long time. The repo moved to OLE long ago. Grub Legacy isn't supported upstream anymore. So...
- What updates *do you get*?
- Why not a more recent version?

---

### Post by doru001 on 2011-12-19
Thank you for your answers. 

> **MAFoElffen said:**
> My Personal Own Curiousity = I used that version server edition when it was released. That server version was current, what, 4 years ago?  8.04 hasn't been supported in a long time. The repo moved to OLE long ago. Grub Legacy isn't supported upstream anymore. So...
- What updates *do you get*?
- Why not a more recent version?
I believe that 8.04 is the current lts version for servers. Support for Desktop 8.04 has been discontinued.

---

