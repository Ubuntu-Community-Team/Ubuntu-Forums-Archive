---
title: "Installing from Linux Format Magazine DVD"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by AnotherMuggle on 2011-07-23
I want to install Eclipse which is almost 200MB to download.  I noticed I have a Linux Format Magazine cover DVD with Eclipse on it.  If I install using the DVD as the source will I get updates through the internet via apt-get?

Cheers,
TK

---

### Post by dino99 on 2011-07-23
add the dvd in sources.list and deactivate the other repo to pick the packages only on it. When done, set the previous config back.

---

### Post by ~!geek!~ on 2011-07-23
I usually avoid using eclipse from repository as I try to have latest eclipse (latest enough). So I download desired eclipse from eclipse.org (latest is 3.6, I  think). 
The usual download is a compressed file which on extracting prduces only one directory named eclipse. Just move this directory somewhere (I prefer /opt/ for keeping this.) Now make a new item in menu and point it to location of eclipse/eclipse executable file. 
So If your cd contains a compressed directory as I described, you may follow my way. To update just go to help and check for updates in eclipse menu. That's it.

---

### Post by AnotherMuggle on 2011-07-24
Thanks both for the useful information :)

---

