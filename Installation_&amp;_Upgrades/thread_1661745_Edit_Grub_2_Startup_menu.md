---
title: "Edit Grub 2 Startup menu"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by Goldpin on 2011-01-07
I'm currently running Lucid Lynx, which installed the Grub 2 Boot loader which it currently lists three different Linux kernels.  My problem is this:

1.  How do I edit the menu to either remove or comment out one or more of the kernels?

2.  Can I remove any of the kernels I don't want, which files do I remove, and will doing so compromise my system.

Thanks in advance for any advice.

---

### Post by presence1960 on 2011-01-07
> **Goldpin said:**
> I'm currently running Lucid Lynx, which installed the Grub 2 Boot loader which it currently lists three different Linux kernels.  My problem is this:

1.  How do I edit the menu to either remove or comment out one or more of the kernels?

2.  Can I remove any of the kernels I don't want, which files do I remove, and will doing so compromise my system.

Thanks in advance for any advice.

To remove unwanted kernels open Synaptic Package Manager. Tick Mark for Removal linux-headers-x.x.xx-xx

Also tick Mark for Removal linux-image-x.x.xx-xx

Click Apply.

Ticking Mark for Removal will uninstall those packages but leave them in cache so if you need to reinstall them you won't have to download them again. To completely get rid of them from your disk tick Mark for Complete Removal. If you then decide to reinstall those packages they will have to be downloaded again.

---

### Post by Goldpin on 2011-01-08
I did as suggested by Presence 1960 and removed the kernels/headers I didn't want and the entries disappeared from the Grub menu.

Success!!!

---

### Post by presence1960 on 2011-01-08
> **Goldpin said:**
> I did as suggested by Presence 1960 and removed the kernels/headers I didn't want and the entries disappeared from the Grub menu.

Success!!!

Glad to be able to help. Enjoy Ubuntu!

---

