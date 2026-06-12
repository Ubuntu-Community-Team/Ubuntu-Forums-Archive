---
title: "internal compiler error: Illegal instruction?"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-10-10
well what do you think?
> scott2@scott2-desktop:~/microdia$ make
make -C /lib/modules/2.6.31-13-generic/build SUBDIRS=/home/scott2/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-13-generic'
  CC [M]  /home/scott2/microdia/sn9c20x-usb.o
/home/scott2/microdia/sn9c20x-usb.c: In function ‘usb_sn9c20x_bulk_init’:
/home/scott2/microdia/sn9c20x-usb.c:367: internal compiler error: Illegal instruction
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.
make[2]: *** [/home/scott2/microdia/sn9c20x-usb.o] Error 1
make[1]: *** [_module_/home/scott2/microdia] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-13-generic'
make: *** [driver] Error 2
scott2@scott2-desktop:~/microdia$ 

---

