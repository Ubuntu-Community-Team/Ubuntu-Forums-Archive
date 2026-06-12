---
title: "Compile and install ivtv drivers"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by handband2 on 2006-06-10
I need a little help if anyone knows...

I'm installing the ivtv drivers for my WinTV Go-Plus (Model 1033) on Kubuntu dapper.

The site I'm using to install the drivers is here:  [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

Everything seems to be going good until I have to compile.  Here is the error I'm getting:

make -C driver install
make[1]: Entering directory `/usr/src/ivtv-0.4.5/driver'
make -C /lib/modules/2.6.15-23-k7/build M=/usr/src/ivtv-0.4.5/driver modules
make[2]: Entering directory `/usr/src/linux-source-2.6.15'
  Building modules, stage 2.
  MODPOST
  CC      /usr/src/ivtv-0.4.5/driver/ivtv-fb.mod.o
  LD [M]  /usr/src/ivtv-0.4.5/driver/ivtv-fb.ko
  CC      /usr/src/ivtv-0.4.5/driver/ivtv.mod.o
  LD [M]  /usr/src/ivtv-0.4.5/driver/ivtv.ko
  CC      /usr/src/ivtv-0.4.5/driver/saa7127.mod.o
  LD [M]  /usr/src/ivtv-0.4.5/driver/saa7127.ko
  CC      /usr/src/ivtv-0.4.5/driver/tda9887.mod.o
  LD [M]  /usr/src/ivtv-0.4.5/driver/tda9887.ko
  CC      /usr/src/ivtv-0.4.5/driver/tuner.mod.o
  LD [M]  /usr/src/ivtv-0.4.5/driver/tuner.ko
  CC      /usr/src/ivtv-0.4.5/driver/tveeprom.mod.o
  LD [M]  /usr/src/ivtv-0.4.5/driver/tveeprom.ko
make[2]: Leaving directory `/usr/src/linux-source-2.6.15'
make INSTALL_MOD_PATH= INSTALL_MOD_DIR=ivtv \
                -C /lib/modules/2.6.15-23-k7/build M=/usr/src/ivtv-0.4.5/driver modules_install
make[2]: Entering directory `/usr/src/linux-source-2.6.15'
  INSTALL /usr/src/ivtv-0.4.5/driver/ivtv-fb.ko
cp: omitting directory `/lib/modules/2.6.15-23-k7'
make[3]: *** [/usr/src/ivtv-0.4.5/driver/ivtv-fb.ko] Error 1
make[2]: *** [modules_install] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.15'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/usr/src/ivtv-0.4.5/driver'
make: *** [install] Error 2

Anyone know how to fix this so I can finish installing? 

Thanks!!

---

