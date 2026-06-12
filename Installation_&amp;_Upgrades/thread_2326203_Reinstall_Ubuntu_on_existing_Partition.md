---
title: "Reinstall Ubuntu on existing Partition"
date: 2016-05-29
forum: Installation &amp; Upgrades
---

### Post by cutano on 2016-05-29
Running duel boot with windows 10/Ubuntu 14.04. Want to reinstall Ubuntu on its partition via USB live iso. Any problems to avoid with swap file and boot loader?

---

### Post by oldfred on 2016-05-29
UEFI or BIOS?
Do you have swap already?

If you use Something Else and choose existing Ubuntu partition with change button, it will over install that partition. You still have to select ext4 & / (root). It will auto find swap if you have it. And default install of boot loader on that screen is to sda, which is correct, unless you have multiple drives.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by ubfan1 on 2016-05-29
Do not choose any "reinstall Ubuntu" option offered by the installer, it will overwrite the whole disk without warning.

---

### Post by SuperFreak on 2016-05-29
> **ubfan1 said:**
> Do not choose any "reinstall Ubuntu" option offered by the installer, it will overwrite the whole disk without warning.

Instead Choose "Something Else"

---

### Post by cutano on 2016-05-30
BIOS not UEFI. Just wanted to make sure I wasnt missing anything. I do install using something else wasnt sure about the swap partition. Thanks

---

