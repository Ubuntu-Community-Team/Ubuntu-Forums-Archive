---
title: "boot menu"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by akhileshtp on 2009-12-14
hi, i am on dual boot with windows. Now in boot menu I get different versions of ubuntu to select from. How do I remove unwanted ones and keep only the latest.regards

---

### Post by pythonscript on 2009-12-14
You need to edit your /boot/grub/menu.lst file, using this command:

```
gksu gedit /boot/grub/menu.lst
``` and enter your password. Near the bottom, you'll see a list of entries; *back up the file before proceeding*. Remove any unwanted entries. Re-install grub.

---

### Post by theozzlives on 2009-12-14
> **akhileshtp said:**
> hi, i am on dual boot with windows. Now in boot menu I get different versions of ubuntu to select from. How do I remove unwanted ones and keep only the latest.regards

Those are just kernels, you should keep the latest two. With legacy GRUB you can just edit the menu.lst, GRUB2 you'll have to remove the kernel in Synaptic and run ```
sudo update-grub
```

---

