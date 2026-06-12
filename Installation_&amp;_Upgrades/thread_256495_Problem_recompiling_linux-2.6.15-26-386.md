---
title: "Problem recompiling linux-2.6.15-26-386"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by elderet on 2006-09-13
When I try to recompile the kernel I get the following error:

# make all
  CHK     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2

Have I missed to install something? I have searched but cannot find any documentation on how to recompile the kernel using ubuntu...

(Installed linux-headers-2.6.15-26-386, linux-image-2.6.15-26-386. Fixed 
/usr/src/linux link. Copied /boot/config-2.6.15-26-386. make oldconfig)

](*,)

---

### Post by Original Brownster on 2006-09-13
Hi there,

It's been a while since I've compiled a kernel, used to do it all the time at one point, anyway to answer your question check this [thread,]("http://ubuntuforums.org/archive/index.php/t-24853.html")   it explains the ubuntu / debian way of compiling a kernel and creating the necessary dpkg, nice and easy. 
Hardest thing I found was doing the initial kernel config as I always always missed some important feature and it wasn't till I rebooted that I found the problem! Then it was a matter of refining the config file until you got it just right, then made sure you had a copy for next time!

HTH


> **elderet said:**
> When I try to recompile the kernel I get the following error:

# make all
  CHK     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2

Have I missed to install something? I have searched but cannot find any documentation on how to recompile the kernel using ubuntu...

(Installed linux-headers-2.6.15-26-386, linux-image-2.6.15-26-386. Fixed 
/usr/src/linux link. Copied /boot/config-2.6.15-26-386. make oldconfig)

](*,)

---

