---
title: "Windows 10 Grub missing after ubuntu install"
date: 2015-09-03
forum: Installation &amp; Upgrades
---

### Post by muhammad11 on 2015-09-03
I had windows 10 installed. I tried to dual boot it with ubuntu 14.04. After installation Ubuntu is running perfectly, but WIndows 10 Grub has gone. I can't load WIndows 10. Only the Ubuntu Grub shows up, which only gives the option of booting ubuntu. I tried boot-repair, but it wasn't successful. Here is the report: [http://paste.ubuntu.com/12268390/](http://paste.ubuntu.com/12268390/). Kindly help me out.

Thanks

---

### Post by powder on 2015-09-03
Try updating grub and see if it finds your Win10 install.
```
sudo update-grub
```

---

### Post by oldfred on 2015-09-03
It shows Windows.
>  'Windows Recovery Environment (loader) (on /dev/sda1)'



I have seen other cases where it seems to think it is the recovery mode not the full install. But your full install of Windows is in sda1, so only description is wrong.

Grub only boots Working Windows, so if not booting, you may need Windows repairs. With all versions of Windows 8 or later you must have fast start up or the always on hibernation off as grub cannot boot hibernated Windows.

---

