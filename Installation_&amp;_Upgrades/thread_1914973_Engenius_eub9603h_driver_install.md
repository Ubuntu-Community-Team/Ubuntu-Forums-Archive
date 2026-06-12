---
title: "Engenius eub9603h driver install"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by paul23 on 2012-01-25
At the moment I'm trying to install a Engenius EUB9603H usb adapter on Ubuntu 10.04 LTS. The kernel I used is 2.6.34.10  (had to use this ubuntu and kernel due to compatibility with the 3350MX e-box pc). The procedure as applied in [http://robosavvy.com/forum/viewtopic.php?p=33206](http://robosavvy.com/forum/viewtopic.php?p=33206) went perfectly.

Now I have the struggle in getting the wireless adapter driver installed. As expected, my ubuntu skills suck. The driver that I wish to get working is [http://www.engeniustech.com.sg/node/277](http://www.engeniustech.com.sg/node/277) (although trying a few different drivers thus far)

So, at the moment when I cd to the specified directory with the makefile in, and type "make", I get:

Makefile:11: /config: No such file or directory
make: *** No rule to make target '/config". Stop.

I also "sudo make" (whatever that means) which gave me the same error, and "make all" which gave me:

Makefile:11: /home/jan/Desktop/EUB-960H: No such file or directory
Makefile:11: -: No such file or directory
Makefile:11: Linux: No such file or directory
Makefile:11: driver/EUB9603H: No such file or directory
Makefile:11: series: No such file or directory
make: *** linux: Is a directory. Stop

Any help would be appreciated please

---

### Post by mafi127 on 2012-03-12
Need help allso whit thows drivers. how can I install it ? I'm running ubunut 11.10 32bit.

---

