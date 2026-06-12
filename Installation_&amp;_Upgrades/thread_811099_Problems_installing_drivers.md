---
title: "Problems installing drivers"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by dahraf77@gmail.com on 2008-05-28
I am trying to install the drivers to my Texas Instrument 5 in 1 card reader, I am using the  tifm drivers and following the directions from [here]("http://ubuntuforums.org/showthread.php?t=797031&highlight=Texas+instruments+card+reader").

When I go to do the make command it get this error message, and I have no idea what it means

```
dahraf77@dahraf77:~/driver$ make
echo /home/dahraf77/driver
/home/dahraf77/driver
make -C /lib/modules/2.6.22-14-generic/build M=/home/dahraf77/driver
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/dahraf77/driver/mspro_block.o
/home/dahraf77/driver/mspro_block.c: In function ‘h_mspro_block_transfer_data’:
/home/dahraf77/driver/mspro_block.c:675: warning: implicit declaration of function ‘sg_set_page’
/home/dahraf77/driver/mspro_block.c:676: warning: implicit declaration of function ‘sg_page’
/home/dahraf77/driver/mspro_block.c:676: error: invalid operands to binary -
make[2]: *** [/home/dahraf77/driver/mspro_block.o] Error 1
make[1]: *** [_module_/home/dahraf77/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

```

Can someone please help with this mess.

Thanks in advance.

---

