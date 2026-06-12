---
title: "kernel upgrade"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by zaidst on 2011-08-04
[SIZE=2]Hey Geeks 

I want to upgrade my kernel from version 2.6.38-10 to 3 
I downloaded the kernel 3 from kernel.org by this command :
***wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-3.0.tar.bz2]("http://www.kernel.org/pub/linux/kernel/v2.6/linux-x.y.z.tar.bz2")*** while i'm in /tmp directory 

and i did these commands also

***$ tar -xjvf linux-2.6.25.tar.bz2 -C /usr/src***[I][B]
 $ cd /usr/src[/B][/I]

till now everything is okay
so now the next step as my manual 
 
$ make gconfig 

that's give me this result 

[/SIZE][SIZE=2][SIZE=2]*
* Unable to find the GTK+ installation. Please make sure that
* the GTK+ 2.0 development package is correctly installed...
* You need gtk+-2.0, glib-2.0 and libglade-2.0.
*
make[1]: *** No rule to make target `scripts/kconfig/.tmp_gtkcheck', needed by `scripts/kconfig/gconf.o'.  Stop.
make: *** [gconfig] Error 2[/SIZE]
 
and the gtk+ is installed correctly but don't know what's wrong exactly .
I wait your help 
Thanks All[/SIZE]

---

### Post by mbobak on 2011-08-04
Try:
```
make menuconfig
```
instead.

-Mark

---

### Post by mbobak on 2011-08-04
Or, better yet, find a ppa, like abogani, that already has 3.0 kernel available for installation.

But, beware, 3.0 is *very* new, and may break stuff.  I can tell you from first hand experience, that it breaks the nvidia-current driver.

I've got a different thread in this forum opened on that issue.

-Mark

---

