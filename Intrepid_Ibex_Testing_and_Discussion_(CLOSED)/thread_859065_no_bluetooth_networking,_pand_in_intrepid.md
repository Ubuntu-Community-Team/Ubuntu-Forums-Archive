---
title: "no bluetooth networking, pand in intrepid?"
date: 2008-07-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by puccaso on 2008-07-14
what is going on
i thought intrepid was supposed to be the networking perfection as far as linux distubutions go..

hardy had pand and it worked perfectly
why would pand and other bluetooth-network or bluez-network stuff be removed from intrepid?

can someone explain to me how i can get pand back into intrepid.. 

cheers.

---

### Post by MALEADt on 2008-07-14
[http://ubuntuforums.org/showthread.php?t=858463](http://ubuntuforums.org/showthread.php?t=858463)
same issue

sounds more like a regression error than a deliberate choice to remove the bluetooth stack.

---

### Post by Eclipse. on 2008-07-14
My guess is its all going to be integrated into NM 0.7.

If you need everything to work you seriously should just be using hardy at this time.

---

### Post by puccaso on 2008-07-15
iv been looking through the nm .7 milestones
and no where do i see bluetooth there?
can u guide me to the right location?

thanks in advance.

---

### Post by plun on 2008-07-16
I am running NM 0.7 but there is no support for Blutooth

Dev link about this and **asacs announcement**

[http://ubuntuforums.org/showthread.php?p=5305173#post5305173](http://ubuntuforums.org/showthread.php?p=5305173#post5305173)

Note on page 18 !!!   Do not install if you dont know howto downgrade.


I am also using Blueman for Blutooth

[http://blueman.tuxfamily.org/](http://blueman.tuxfamily.org/)

the bluez-network must be installed separate.

All packages within intrepids repo
[http://packages.ubuntu.com/search?suite=intrepid&arch=any&searchon=names&keywords=bluez](http://packages.ubuntu.com/search?suite=intrepid&arch=any&searchon=names&keywords=bluez)


I am trying to figure out * Bind services to /dev/rfcomm ports, for eg. connecting via gprs, for a 3G phone.

Using wvdial for the moment.

---

