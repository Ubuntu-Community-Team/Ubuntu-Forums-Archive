---
title: "How to compile a 32bit kernel on a 64bit linux"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by vlitzer on 2007-09-08
I have my main pc runing ubuntu feisty 64, i want to compile on it the kernel of my old laptop wich is running xubuntu feisty 32. I tried following this exelent guide ( [link]("http://www.howtoforge.com/kernel_compilation_ubuntu")) and obviosly fail to load the .config with errors. So i read a litle and run:

```
make menuconfig -ARCH=i386

```
and i manage to pass this stage without problems. Once i saved the kernel configuration is when i need a litle help.

```
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers 

```
wont run.
```

fakeroot make-kpkg --initrd --arch i386 --append-to-version=-custom kernel_image kernel_headers
```

wont run either.. so i guess i need some special version of kernel libs or perhaps gcc? 

any clues about this? thanks in advance!

Bruno

---

