---
title: "self made kernel modules too big."
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by h113331pp on 2012-06-21
Hi guys:
    This is embarrassing, but I have a problem for building kernel modules. 

    I install all stuff and "apt-get source linux-source", copy the config file, and "make modules".

    and after taking a very long time to wait, I got my kernel installed by "make modules_install".

the modules could work correctly, but is one thing weird - it`s very big :(

for example:  the fat.ko in ubuntu 12.04 livecd is about 70KB but my fat.ko is about 900KB.

I wonder what I do wrongs, could someone please teach me the right way to build the kernel modules?  

sorry for my awful English grammar, I`m not a native speaker.

p.s: I also tried strip the modules by "strip fat.ko", but it`s failed, the kernel will unable to modprobe it.

---

### Post by dino99 on 2012-06-21
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

[http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/](http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/)

[http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html](http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html)

---

### Post by h113331pp on 2012-06-21
to dino99:
    I appreciate your informations, and my method is exactly the same as your second URL link. 
    I noticed that the first URL link say ubuntu has a different way to build the modules by "make-kpkg", would this method could shrink the size of the modules file?

I got why I do wrong, just strip "only" debug symbol, and that would be fine.

I reffer to this link:

[http://unix.stackexchange.com/questions/25421/how-much-strip1-ing-is-okay-for-kernel-modules](http://unix.stackexchange.com/questions/25421/how-much-strip1-ing-is-okay-for-kernel-modules)

---

