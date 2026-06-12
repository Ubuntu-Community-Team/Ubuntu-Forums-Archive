---
title: "network card installation problem please help"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by grooverider on 2008-05-29
i run ubuntu hardy and have a p5gc asus motherboard, with a nic on board it is the r8168. the problem is commonly known that it does not work right out of the box, there is a fix for it, but only works with kernel 2.6.24-16 and i got the 2.6.24-17 and it does not work anymore. i have found this site:
[http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)
the author was so nice to offer precompiled drivers for 2.6.24-17 but i got no clue how to install them, can anyone please help? thx in advance :)

addition: these are the steps i follow from the readme in the tarball and i get this:
sorry to bother again, i downloaded the tarball, did:

rmmod r8169

depmod -a

cp r8168_scripts/precompiled/r8168.ko.v6.17-generic \

/lib/modules/2.6.24-17-generic/kernel/drivers/net/r8168.ko

then did

insmod r8168.ko

but get an error:

insmod: error inserting &#8216;r8168.ko&#8217;: -1 Invalid module format

what am I doing wrong? thx for the help again

---

