---
title: "Help with make-kpkg in server !!!"
date: 2006-03-18
forum: Installation &amp; Upgrades
---

### Post by thehose on 2006-03-18
Just installed Server 5.10 (ASUS K8N-DL,Opterons 246 and 4Gb RAM) and ALL went well. However now I try to customize the kernel and the "make-kpkg modules_image" barfs (attached) all over the console. The following are the steps I performed according to what I read in this forum:

1.apt-get install linux-tree
2.apt-get install build-essential
3.apt-get install kernel-package
4.apt-get install gcc
5.apt-get install gcc-3.4
6.apt-get install libncurses5
7.apt-get install libncurses5-dev
8.apt-get install libqt3-mt-dev
9.cd /usr/src
10.tar --zip2 -xvf  linux-source-2.6.xx.tar.bz2
11.ln -s /usr/src/linux-source-2.6.xx /usr/src/linux

And these steps to create the new kernel package:

1.cd /usr/src/linux
2.make-kpkg clean
3.make-kpkg --revision=1.0.0 --append-to-version=. 20060316 kernel_image

Step 3. creates the .deb package OK.

4.make-kpkg --revision=1.0.0 --append-to-version=. 20060316 modules_image

What did I miss along the way ?????

---

### Post by ranf on 2006-03-19
2.5 make menuconfig (or xconfig)

There are HowTo's here in the forums and in the wiki.

Edit: I just read up on the target modules_image with "man make-kpkg"
```

       modules_image
              This  target  allows you to build all packages under MODULE_LOC,
              which defaults to /usr/src/modules,  but  does  not  create  the
              source  or  diff  files,  and does not create and sign a changes
              file. This is the only modules related option you  need  if  you
              just  want to compile the add on modules image files for instal-
              lation on one or more machines. Generally called in  conjunction
              with   kernel_image,   especially   if  also  using  the  option
              append_to_version (prevents spurious warnings).

```

---

### Post by thehose on 2006-03-20
So is this analogous to 'make modules_install' on other distros like Gentoo ??
Is what I'm getting on the console an error, warning, ???

---

### Post by ranf on 2006-03-21
[QUOTE=thehose]So is this analogous to 'make modules_install' on other distros like Gentoo ??
[/QUOTE]
No. It is not needed. 
make-kpkg has already put the modules into the .deb in /usr/src.

---

