---
title: "Is it possible to install with grub1?"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Zalbor on 2009-10-28
It's basically in the title... If I do a clean install of 9.10, is it possible to ask it to use the old grub instead of grub2?

I read that grub2 doesn't yet have the password/lock feature, and that's mandatory for me.

---

### Post by whoop on 2009-10-28
Don't think it is. It should be possible to revert back to grub1, after installation. I've done this unintentionally while karmic was in alpha.
But more interestingly what are your problems with grub2?

---

### Post by Zalbor on 2009-10-28
If I do revert after the installation, will it work like it does now (in 9.04 and previous versions)?

I'm basically asking about menu.lst changing automatically after installing/removing kernels, or at least by using update-grub, and the "commented" instructions in menu.lst.

---

### Post by philinux on 2009-10-28
[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy)

See the bug report re password and lock,

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392158](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392158)

---

### Post by xebian on 2009-10-28
> **Zalbor said:**
> It's basically in the title... If I do a clean install of 9.10, is it possible to ask it to use the old grub instead of grub2?

I read that grub2 doesn't yet have the password/lock feature, and that's mandatory for me.

Absolutely.  Just did a fresh install and it will ask you which loader you want.

There are many ways to do it.  One way is to not install a loader during the installation, and then boot from an old loader.  Once in, install your grub1, then make it the boot loader for your system.

---

### Post by Zalbor on 2009-10-28
Alright, this all sounds good then! Thanks for your replies.

---

### Post by dino99 on 2009-10-28
follow this thread:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

---

