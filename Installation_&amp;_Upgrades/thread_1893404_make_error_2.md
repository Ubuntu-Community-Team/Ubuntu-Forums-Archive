---
title: "make error 2"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by dirkwillem on 2011-12-10
Hello;

I´m trying to install DevkitAdvance from a makefile. When I tried it the first time it gave a busload of code, wich I can see anymore. It at least had an error. When I try to install again, I get this:

```
dirk@ubuntu:~$ cd /home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/
dirk@ubuntu:~/Bureaublad/GBA/DevkitAdvance/devkitadv$ make
make -w install-binutils
make[1]: Entering directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv'
( \
STRIPPROG=/usr/bin/strip; \
cd build-binutils && \
make -w install INSTALL_PROGRAM_ARGS="-s" \
)
make[2]: Entering directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils'
/bin/sh ../binutils-2.12.1/mkinstalldirs /usr/local/devkitadv /usr/local/devkitadv
mkdir /usr/local/devkitadv
mkdir /usr/local/devkitadv
make[2]: *** [installdirs] Error 1
make[2]: Leaving directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv/build-binutils'
make[1]: *** [install-binutils] Error 2
make[1]: Leaving directory `/home/dirk/Bureaublad/GBA/DevkitAdvance/devkitadv'
make: *** [stmp-binutils-make-install] Error 2
dirk@ubuntu:~/Bureaublad/GBA/DevkitAdvance/devkitadv

```

Does anyone know how to solve this?
Any help is appreciated

DirkWillem

---

