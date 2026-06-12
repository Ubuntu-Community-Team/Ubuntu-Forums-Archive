---
title: "Compiling kernel 2.6.37.2"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by yeketaz on 2011-03-04
Hi
I want when I compile my kernel 2.6.37.2 when handling a make I see this error message please help :-(
```
root@mahdi-laptop:/home/mahdi/Desktop/linux-2.6.37.2# make -j4/home/mahdi/Desktop/linux-2.6.37.2/arch/x86/Makefile:81: stack protector enabled but no compiler support
gcc: Command not found
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CC      scripts/mod/empty.o
gcc: not found
make[2]: *** [scripts/mod/empty.o] Error 127
make[1]: *** [scripts/mod] Error 2
make[1]: *** Waiting for unfinished jobs....
make: *** [scripts] Error 2
make: *** Waiting for unfinished jobs....
  CC      kernel/bounds.s
gcc: not found
make[1]: *** [kernel/bounds.s] Error 127
make: *** [prepare0] Error 2

```

---

### Post by ryezs on 2011-03-04
You need to install gcc. Run
```
sudo apt-get install gcc
```

---

### Post by yeketaz on 2011-03-04
gcc was already installed, which gives this error

---

### Post by wojox on 2011-03-04
You have **build-essentials** installed?

You can also download the .debs [amd64 build of linux-meta 2.6.37.2.4 in ubuntu]("https://launchpad.net/ubuntu/+source/linux-meta/2.6.37.2.4/+buildjob/2041215")

---

