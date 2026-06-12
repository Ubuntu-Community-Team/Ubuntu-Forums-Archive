---
title: "Modem Support"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by jam1 on 2006-07-07
Hi guys,
I'm currently in the process of downloading Ubuntu 6.06 LiveCD and I have a question.

My ADSL modem a PCI one (internal), Samsung AHT-N120.
- I have tried and tried googling for drivers support regarding Linux and this modem and have found **nothing**.
- IRC "tech support" did not yield any results either.

How am I going to get my internet connectivity up-and-running with Linux (in this case, with the Ubuntu distro) and this modem?! :confused: 

Obvioulsy w/out inet access this switch attempt will be useless and I do want to switch! :evil: 

Thanks for all who might help!]
(and please don't tell me to switch modems, this is currently not an option)

---

### Post by shultzjr on 2006-07-07
Hi guys,
I'm currently in the process of download Ubuntu 6.06 LiveCD and I have a question.

My ADSL modem a PCI one, Samsung AHT-N120.
- I have tried and tried googling for drivers support regarding Linux and this modem and have found nothing.
- IRC "tech support" did not yield any results either.

How am I going to get my internet connectivity up-and-running with Linux (in this case, with the Ubuntu distro) and this modem?! 

If you "modem" is like my DSL box, you need an ethernet connection.  Just set your ethernet connect to dhcp and it should work.

charles.....

PS.  To me, if it has an RJ-45 it is NOT a modem.

---

### Post by shultzjr on 2006-07-07
Sorry, missed the PCI part.

Assumption, your dsl provider sent you the pci device and it only works with Windows type computers.  I bet that if you can't find a driver for the "modem" you'll be out of luck.  My dsl provider sent me an external box that had 3 connectors: one for power, one for the incomming phone line and one for the ethernet connection that I connect a WRT54G into.  Externals are ugly but they do work better with Linux in this case.

later.....

PS.  To get multiple computers under your scenario, you'll have to use a Windows box as a gateway.  The only other configuration that will work is to connect one Windows box to the dsl line and that will be your Internet connection, viruses and all.

---

### Post by jam1 on 2006-07-07
I have edited my original post.
My modem is an internal modem, just like the old dial-up modems that you hook up your phone line to, only this one is an ADSL one...

Last time I tried switching (4 years ago, Mandrake 9 :)), I had no success with this modem and am just worried I might still not have any luck...

--
We posted together. ;)

bleh.
So even if this modem will work this time around, I won't be able to hook up my other box (WinXP) so it'll have inet access as well? (currently I achive this by a simple wire between the two machines)

sigh.
Life's so complicated. :)

---

