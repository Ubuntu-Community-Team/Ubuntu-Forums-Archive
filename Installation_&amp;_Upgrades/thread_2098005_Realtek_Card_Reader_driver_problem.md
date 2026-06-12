---
title: "Realtek Card Reader driver problem"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by S3rgeant Mark on 2012-12-25
Hi! I bought a new sleekbook HP Envy 14 and stucked with Card Reader, which doesn't recognize any cards. OS - Ubuntu 12.10. At previous system, Windows 8, card reader worked fine. So I decided, that problem in Card Reader driver. I downloaded the driver for Linux from the Realtek site and try to install it, it was in tar.bz2 archive. So I extracted driver from archive, then type "make" in terminal and get this:

cp -f ./define.release ./define.h
make -C /lib/modules/3.5.0-21-generic/build/ SUBDIRS=/home/yan/realtek/rts5229 modules
make[1]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/usr/src/linux-headers-3.5.0-21-generic'
  CC [M]  /home/yan/realtek/rts5229/rtsx.o
  CC [M]  /home/yan/realtek/rts5229/rtsx_chip.o
  CC [M]  /home/yan/realtek/rts5229/rtsx_transport.o
  CC [M]  /home/yan/realtek/rts5229/rtsx_scsi.o
  CC [M]  /home/yan/realtek/rts5229/rtsx_card.o
  CC [M]  /home/yan/realtek/rts5229/general.o
  CC [M]  /home/yan/realtek/rts5229/sd.o
  CC [M]  /home/yan/realtek/rts5229/ms.o
  LD [M]  /home/yan/realtek/rts5229/rts5229.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/yan/realtek/rts5229/rts5229.mod.o
  LD [M]  /home/yan/realtek/rts5229/rts5229.ko
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/usr/src/linux-headers-3.5.0-21-generic'

But when I type "make install", I get:
cp rts5229.ko /lib/modules/3.5.0-21-generic/kernel/drivers/scsi -f
cp: impossible create file «/lib/modules/3.5.0-21-generic/kernel/drivers/scmsi/rts5229.ko»: Access denied
make: *** [install] Error 1


What I did wrong?

---

### Post by dino99 on 2012-12-25
maybe you have already heard about sudo and modprobe

[http://askubuntu.com/questions/189847/lenovo-thinkpad-l530-sd-card-reader-not-working](http://askubuntu.com/questions/189847/lenovo-thinkpad-l530-sd-card-reader-not-working)

---

### Post by S3rgeant Mark on 2012-12-25
Thanks, problem solved. In your link is not same problem as I had, there a RTS 5229 card reader and I have RTS 5289. But then I found the thread with the same card reader and driver, which works fine for me. 

[http://forums.gentoo.org/viewtopic-t-922794-start-0.html](http://forums.gentoo.org/viewtopic-t-922794-start-0.html)

Thanks dino99!

---

