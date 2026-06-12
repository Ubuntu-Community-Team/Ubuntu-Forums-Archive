---
title: "Problems with network card"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by LusiphurScyla on 2005-04-14
cnf401 de CNET...
Its a PCMCIA card...
Any advices about where to get the drivers?
IN the hoary distribution does not work...the network connection does not work.

Salutes

Please, some one answer.

---

### Post by speedman on 2005-04-14
The output from:

cardctl ident

... would probably provide clues with regards to identifying the proper module for the card - if one exists.


Regards,

SM

---

### Post by LusiphurScyla on 2005-04-15
Cool man! its a realtek rtl8139!!!
But i was working in the internet for finding this card. I found it. But it is for compiling. I know (or i can deduce) how to compile it, but...after it...were i put it??

The url is [http://www.scyld.com/driver_updates.html](http://www.scyld.com/driver_updates.html)

p.d.>the command cardctl....can be used in others ways?

---

### Post by speedman on 2005-04-15
[QUOTE=LusiphurScyla]Cool man! its a realtek rtl8139!!![/QUOTE]

Excellent.  That is a common chipset.

> But i was working in the internet for finding this card. I found it. But it is for compiling. I know (or i can deduce) how to compile it, but...after it...were i put it??

The url is [http://www.scyld.com/driver_updates.html](http://www.scyld.com/driver_updates.html)

That url is for a driver for 2.4.x kernels and previous versions.  It is not applicable for Ubuntu unless you have specifically installed a 2.4 kernel on your system.

Typically for pcmcia cards with the rtl8139 chipset you need to load the following two modules:

8139cp & mii

That being said the 8139too module will work for some rtl8139 based pcmcia nics.

You can try this:

sudo modprobe 8139cp mii

... and then try to configure your nic.  If those modules don't cooperate do this:

sudo rmmod 8139co mii

sudo modprobe 8139too

... and try your nic again.  When you settle on which modules you wish to use simply add them to the end of the /etc/modules file to have them automatically load each time your system boots.

> p.d.>the command cardctl....can be used in others ways?

Absolutely.  If you run cardctl with root privs it will expose much more functionality.  man cardctl for more information.  You may also be interested in the cardinfo utility, which is installed suid root by default, so normal users can manipulate pcmcia cards in a limited manner from a gui app.


Regards,

SM

---

