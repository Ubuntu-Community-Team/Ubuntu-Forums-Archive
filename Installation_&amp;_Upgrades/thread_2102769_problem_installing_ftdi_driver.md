---
title: "problem installing ftdi driver"
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by haresh chavda on 2013-01-08
dear all , i'm have installed vm ware on my windows xp (32bit) machine.
 then i have installed ubuntu 12.04LTS in that. it is working fine.
now i want to run beaglebone with this.

it requires to install FTDI ,USB to serial driver.
i have downloaded it from site : [http://www.jayconsystems.com/em-18-rfid-reader.html](http://www.jayconsystems.com/em-18-rfid-reader.html)
it is in ".tar.gz" format.
i have extracted this with "tar -xzvf " in "/usr/local/src/"
and run "make".

but it gives fatal error

     

                                                >  h@ubuntu:/usr/local/src/ftdi_sio$ make
gcc -Wall -D__KERNEL__ -DMODULE  -I/lib/modules/3.2.0-29-generic-pae/build/include -D__SMP__ -DSMP  -DMODVERSIONS -include  /lib/modules/3.2.0-29-generic-pae/build/include/linux/modversions.h  -I/usr/src/linux-3.2.0-29-generic-pae/drivers/usb/serial/ -O   -c -o  ftdi_sio.o ftdi_sio.c
cc1: fatal error: /lib/modules/3.2.0-29-generic-pae/build/include/linux/modversions.h: No such file or directory
compilation terminated.
make: *** [ftdi_sio.o] Error 1                            please let me know how to install this driver.
driver folder only contains following files,

 
                                                >  h@ubuntu:/usr/local/src/ftdi_sio$ ls
ftdi_sio.c  ftdi_sio.h  Makefile  Rules.make                                 it does not have config file or *.sh file.
i have already posted this on beginners section but might be wrong place, so creating thead here also.

---

