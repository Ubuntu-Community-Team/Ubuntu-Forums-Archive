---
title: "Kernal error"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by Yizi on 2009-11-29
Hi,

I have just installed Ubuntu on my Netbook (Samsung NC10), after the installation when i booted it up it came up with.

```
error: You need to load the kernal first.
Press any key to continue...
```

---

### Post by mikeac72 on 2009-11-29
Try reinstalling it.  That normally happens after messing around with the Ubuntu partition, or after a failed installation.  Trust me, it happened to me three times.

---

### Post by Yizi on 2009-11-29
I have done it 3 times now, should i do more?

---

### Post by j2bv16 on 2009-11-29
Try download a new kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")
and install

---

### Post by Yizi on 2009-11-29
which one do i choose? is there any tutorial on how to install it?

---

### Post by j2bv16 on 2009-11-29
well, download the lastest ( sorry my english ) 2.6.31.6 is in deb format, download it for your procesot i386 o amd64 ( uname -a in a terminal )

---

### Post by Yizi on 2009-11-29
OK i downlaoded it and i did the uname -a it came back with 2.6.31-14-generic.
I put the file in the memory stick and booted into live CD enviroment and tried to install the debian kernal i downloaded but it said:

Error: Dependency is not satisfiable: linux-headers-2.6.32-020632rc8

---

### Post by j2bv16 on 2009-11-29
> **Yizi said:**
> OK i downlaoded it and i did the uname -a it came back with 2.6.31-14-generic.
I put the file in the memory stick and booted into live CD enviroment and tried to install the debian kernal i downloaded but it said:

Error: Dependency is not satisfiable: linux-headers-2.6.32-020632rc8

download the dependency  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc8/linux-headers-2.6.32-020632rc8_2.6.32-020632rc8_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc8/linux-headers-2.6.32-020632rc8_2.6.32-020632rc8_all.deb)

first install Linux header
2 - Linux Header Generic
3 - Linux Image

---

### Post by j2bv16 on 2009-11-29
I found this [http://ubuntuforums.org/showthread.php?t=830795](http://ubuntuforums.org/showthread.php?t=830795) 
is a grub error, i found a solution but is for arch linux
maybe it help you [http://bbs.archlinux.org/viewtopic.php?id=63411](http://bbs.archlinux.org/viewtopic.php?id=63411)

---

### Post by Yizi on 2009-11-29
Install both and it still says the same error! any ideas?

---

### Post by j2bv16 on 2009-11-30
You will need reinstall the sistem, if the problem persis download a new image of ubuntu

---

