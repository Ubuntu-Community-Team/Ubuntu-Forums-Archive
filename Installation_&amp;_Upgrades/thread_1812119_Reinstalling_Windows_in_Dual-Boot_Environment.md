---
title: "Reinstalling Windows in Dual-Boot Environment"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by mgthantzin on 2011-07-25
I've installed Ubuntu on a Windows 7 PC in dual-boot mode. (But, I primarily use Ubuntu.) I use Windows only when I need to. And, I noticed that my Windows was getting slower and slower and slower. So, I decided to reinstall (format partition and fresh install) Windows 7 again. But, I heard that the boot record could get overwritten by Windows installation.

What precautionary measures should I take to keep my nice-and-fast Ubuntu intact? I do not wish to install Ubuntu again as I like all my current Ubuntu configuration and setup.

Any walk-through link or tutorial blog post would be greatly appreciated.

Peace:
KZee

---

### Post by LemursDontExist on 2011-07-25
When you reinstall windows it will override grub - but shouldn't affect your Ubuntu installation in any other way.  You'll then need to [reinstall grub]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2").  Reinstalling grub really isn't a big deal - I find it takes about 10 minutes.

---

### Post by mgthantzin on 2011-07-25
@LemursDontExist

Thank you so much for such quick response. And, yep! you did answer my question.

I really like the way this community stands. (=

Have a good day.

Peace~
KZee

---

