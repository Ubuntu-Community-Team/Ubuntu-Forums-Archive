---
title: "build small linux from scratch"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by damvcoool on 2007-03-10
ok here is the deal. I have a very old laptop Toshiba Satellite pro 425 CDS that has Pentium 66Mhz, 48MB Ram, 500MB HDD, Floppy Drive, and speakers.

To tell the truth i found it on the garbage.

I want to install linux on it, but i want to make it from scratch and using Busybox, uclibc, and a good kernel.

now Does anyone know how to do this, or at least point me to a uptodate and very easy to follow tutorial. if you can post all the steps here would be a lot better.

I already know how to compile busybox, and uclibc but i dont know what to do after that, also i dont know what to enable from the kernel or what to disable. I want to be able to use openbox as window manage, and python as scripting language(maybe i can use lua if gives better performance). basically i want to do this to learn more about linux and the inner working. i already tried LFS but I cannot understand a damn thing.


Thank you in advance

---

### Post by confused57 on 2007-03-10
I had to search for it, but maybe this will give you some ideas:
[http://www.ubuntuforums.org/showthread.php?t=361348](http://www.ubuntuforums.org/showthread.php?t=361348)

---

### Post by shifan on 2007-03-11
try this

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by damvcoool on 2007-03-13
I already Tried LFS but It never uses busybox and uclibc for the base system it is based on glibc and the normal utilities and i tried but somethings just dont apply and the system is not even bootable.

i also tried buildroot but it has no new stable version and everytime i build something it has one or other thing broken

---

### Post by wonk-o-matic on 2007-03-14
Damn Small Linux

---

### Post by damvcoool on 2007-03-20
i cannot use Damn Small linux the laptop does not have a CD nor a USB only Floppy. I can transfer every file over floppy i have time. Can anyone please help me?? :D

---

### Post by damvcoool on 2007-03-26
An update of how far have i advance on my learnings.

First of all now i know i need a toolchain, that is composed by a c library a c compiler, and some tools like ld(linker) and as(assambler) i know that busybox comes with those, so busybox can create a toolchain with uclibc, but in order to create a busybox compiled with uclibc i need a previously compiled compiler with uclibc, and uclibc 0.9.28 does not come with a c compiler of any form.

HELP!!

---

### Post by Dimebag999 on 2007-04-06
if you want DSL on that laptop - but don't have a CD drive - you can still install nero or a similar burner . Then - (this is what i did) follow these steps;

1.  Download (or transfer by floppy (lol) the .iso for DSL

2. Then use nero to burn the .iso, but to a VIRTUAL DRIVE

3. Then use the installer or live CD thingy, running from the VIRTUAL DRIVE

good luck

---

### Post by damvcoool on 2007-04-08
ok how am i gonna run a virtual Drive without an OS on that laptop??

I am already running DSL but i got other way to do it. I copy the content of the CD and the i boot up with a floppy made in dsl.

but my point is to make a something froms scratch :D can anyone help me :D i want to use uclibc, busybox and tcc. maybe LUA and FLTK as scripting language and and graphical toolkit :D

---

### Post by damvcoool on 2007-04-11
Finally after lots of time spended on internet :D i found something usefull :D alpine linux has a toolchain environment ready to use. also the developer has explained to me how to make my own step by step :D that should end this post :D

---

