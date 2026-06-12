---
title: "installing new kernel without complete dist-upgrade"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by martinko01 on 2007-01-09
what is the quickest way to install a new compiled kernel (in my case: 2.6.20) without touching the rest of the installation ?

can I do something like
 apt-get -t feisty kernel-package ?

if possible, I would like to avoid to compile a new kernel myself from source, and I would also like to avoid to upgrade *completey* to feisty by replacing edgy by feisty in sources.list

---

### Post by hal10000 on 2007-01-09
Where did you get the kernel from? Is it a deb package? Did you compile it?

If you have a precompiled kernel which is provided as a *.deb package, then you can install it simply by using [COLOR="Red"]dpkg -i /your/new/kernel-2.6.10-whatever.deb[/COLOR]

If you got a *.tar.gz (or *.bz2) file then it's usually source code and you have to compile it. You can then make the newly compiled kernel a deb package and install it with dpkg.

---

### Post by JesseWelling on 2007-01-23
I've downloaded the 2.6.18 kernel and applied ingo molnar's -rt7 patch for 2.6.18.
I reused my old config file and then just enabled more of the rt options.

right now i just ran make-kpkg.

my question is about what to do next.
From what I can understand all I have to do is dpkg -i the .deb and everything
will be set up with grub and all modules installed? is it that easy?

---

### Post by hal10000 on 2007-01-24
Yes, it's that easy.

---

