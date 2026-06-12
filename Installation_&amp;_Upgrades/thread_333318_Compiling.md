---
title: "Compiling"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by aiduciukas on 2007-01-07
Hi! When I want to compile something, like kernel... It shows error 2:
/usr/src/modules/fglrx/firegl_public.c: In function ‘firegl_stub_open’: 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:579: warning: assignment discards 
 &#9474; qualifiers from pointer target type
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_request_irq’:
 &#9474; /usr/src/modules/fglrx/firegl_public.c:2568: warning: passing argument 2 
 &#9474; of ‘request_irq’ from incompatible pointer type  
 &#9474;   LD [M]  /usr/src/modules/fglrx/fglrx.o 
 &#9474;   Building modules, stage 2.
 &#9474; /usr/src/linux-headers-2.6.17-10-generic/scripts/Makefile.modpost:42:
 &#9474; include/config/auto.conf: No such file or directory
 &#9474; make[2]: *** No rule to make target `include/config/auto.conf'. Stop.
 &#9474; make[1]: *** [modules] Error 2
 &#9474; make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
 &#9474; make: *** [build] Error 2   

And when I want to compile C++ script it shows error 2 too. what I need do? ](*,) 
Sorry for my poor english :???:

---

### Post by teaker1s on 2007-01-07
You will need to install the essential build files to compile the driver:

user@ubuntu:~$ sudo apt-get update 
user@ubuntu:~$ sudo apt-get install build-essential

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build


Make the driver with the commands "make distclean", "make", and "make install":
 make distclean
 make
 sudo make install

---

### Post by aiduciukas on 2007-01-07
but earlier I did the same, but now i can't do it :( and one more thing it can't find include/config/auto.conf

---

### Post by teaker1s on 2007-01-07
not sure it could possibly require  package installed
[COLOR="Red"]sudo apt-get install autoconf[/COLOR]

other than that source building isn't a strong point so I'm not ignoring you- I just don't know the answer

---

### Post by aiduciukas on 2007-01-07
no :( it isn't working, same error, but earlier I was able to compile, I've compiled these drivers :???:

---

