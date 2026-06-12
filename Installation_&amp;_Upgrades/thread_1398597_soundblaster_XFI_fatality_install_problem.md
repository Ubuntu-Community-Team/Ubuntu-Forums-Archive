---
title: "soundblaster XFI fatality install problem"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by firestond on 2010-02-04
I pretty new to Linux, and am currently learning it in school, but i ahvent been able to get any sound out of my sounblaster card. I have tried a few stickies on these forums and have tried a lot of different things from google results but nothing worked. 
I'm using ubuntu 9.10 and i have downloaded the driver from creative lab XFiDrv_Linux_Public_US_1.00.tar.gz and when i use the sudo make command i get these errors

```
make -C /lib/modules/2.6.31-17-generic-pae/build M=/home/clay/Downloads/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic-pae'
  CC [M]  /home/clay/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/clay/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/clay/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/clay/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/clay/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/clay/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/clay/Downloads/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic-pae'
make: *** [all] Error 2
```
and when i use sudo make install i get

```
Copy module files...
cp: cannot stat `ctxfi.ko': No such file or directory
make: *** [install] Error 1
```any help would be appriciated

---

