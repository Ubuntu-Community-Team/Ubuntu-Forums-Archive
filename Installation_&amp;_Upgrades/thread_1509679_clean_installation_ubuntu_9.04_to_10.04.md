---
title: "clean installation ubuntu 9.04 to 10.04"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by amirmku on 2010-06-14
Hi guys,
I have dual boot Windows XP and ubuntu 9.04. I wish to install ubuntu 10.04 from Live CD. Can anyone tell the way to do. Will GRUB detect the live CD?

Do I need to uninstall Ubuntu 9.04 first or I can overwrite it while installing 10.04? Earlier i had assigned 90GB space in directory F for ubuntu 9.04.

Please help me as I m new to ubuntu.

Thanks in advance.

---

### Post by darkod on 2010-06-14
Directory F? You mean partition F: ?

Did you install wubi inside windows, not full ubuntu?

In that case you are not running grub2 at all, and as far as I know you can't have two different versions of wubi at the same time. You will need to boot wubi 9.04 and copy all the data you want to save from it, then uninstall it from Programs like any other application.

After that you should be able to install wubi 10.04.

---

### Post by amirmku on 2010-06-14
> **darkod said:**
> Directory F? You mean partition F: ?

Did you install wubi inside windows, not full ubuntu?

In that case you are not running grub2 at all, and as far as I know you can't have two different versions of wubi at the same time. You will need to boot wubi 9.04 and copy all the data you want to save from it, then uninstall it from Programs like any other application.

After that you should be able to install wubi 10.04.


No Bro I hav installed ubuntu in  F partition. its definitely not WUBI

---

