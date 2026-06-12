---
title: "Fujitsu P series Touchscreen driver hangs X in Intrepid"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Syock on 2008-10-11
My notebook is Fujitsu FMV-BIBLO Loox P70U/V. FYI, Fujitsu Loox P70 is basically the Japanese version of Fujitsu Lifebook P series (P1510,P1610 etc) you see in western nations.

I think my model uses serial connection for its touchscreen, accessible through /dev/ttyS0. I use the driver provided in [www.conan.de/touchscreen/p-series.html](www.conan.de/touchscreen/p-series.html)

After an upgrade to Intrepid, I can no longer start any X session. I downgraded xserver-xorg to the one in Hardy, there it works again. But I suspect some other trouble in X.org that's fixed by 7.4

Question: Anyone tried running P1510/P1610 on Intrepid (X.org 7.4)? Successful in getting X to start?

I suppose this should go to Intrepid testing board, but I wonder if anyone else here tried X.org 7.4 yet

EDIT:

Fixed the problem by removing/replacing references to old functions/header files in xorg.

Borrowing steps from here, [http://ubuntuforums.org/showthread.php?t=441723&page=4](http://ubuntuforums.org/showthread.php?t=441723&page=4) 
wget 
* Download and extract source from:
[http://www.conan.de/touchscreen/xf86-input-fujitouch-0.6.5.tar.bz2](http://www.conan.de/touchscreen/xf86-input-fujitouch-0.6.5.tar.bz2)

* In source directory:
```

sed -i '/xf86AlwaysCore/d' fujitsu.c
sed -i '/ansic/d' libtouch.c
sed -i 's/xf86memset/memset/' libtouch.c
./configure --prefix=/usr && make && sudo make install

```

* Follow steps 1 & 2 as shown in [http://www.conan.de/touchscreen/p-series.html](http://www.conan.de/touchscreen/p-series.html)
(my default Intrepid installation didn't have "ServerLayout" section though?)


Special thanks to [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/254848](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/254848) for the xf86memset idea.

---

