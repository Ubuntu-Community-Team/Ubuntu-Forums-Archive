---
title: "[SOLVED] Ubuntu 8.10 intrepid"
date: 2008-08-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2008-08-24
My w| restricted driver for my wireless network card is missing after I installed intrepid Alpha 4 please help is there        a way to get the hardy driver back?

---

### Post by spiderbatdad on 2008-08-24
please post the type of wireless card, or run command```
sudo lshw -C net
```and post the output here.

---

### Post by Sef on 2008-08-24
Moved to Intrepid Ibex Testing and Discussion.

---

### Post by autocrosser on 2008-08-24
There is going to be a big kernel change within the next couple of days--the .27 is coming in & a large number of new drivers will be included. Look in the forum for the kernel thread & follow the links. If your driver is not there, you will have to pull it from Hardy.

---

### Post by theozzlives on 2008-08-24
> **spiderbatdad said:**
> please post the type of wireless card, or run command```
sudo lshw -C net
```and post the output here.

=1.21 duplex=full firmware=N/A ip=192.168.0.10 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

---

### Post by autocrosser on 2008-08-24
Well-I see some "possible" help for you--look at: [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

---

### Post by theozzlives on 2008-08-25
> **autocrosser said:**
> Well-I see some "possible" help for you--look at: [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

thanks but what am I supposed to do with that???

---

### Post by spiderbatdad on 2008-08-25
your driver is in synaptic package manager b43-fwcutter. Or you can do ndiswrapper [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
You will have to replace "hardy" with "intrepid" where necessary. There are quite a few tutorials for ndiswrapper with your card.

---

### Post by theozzlives on 2008-08-27
> **spiderbatdad said:**
> your driver is in synaptic package manager b43-fwcutter. Or you can do ndiswrapper [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
You will have to replace "hardy" with "intrepid" where necessary. There are quite a few tutorials for ndiswrapper with your card.

my cards are built in it's a laptop

---

### Post by Gina on 2008-08-27
I have a Broadcom bcm4306 rev 3 chipset in my wireless adapter and that's working fine in Intrepid.  

Ahhh... Just looked back up the thread and see we're talking about a 4310 - I think I read that that model is not yet supported directly so I guess it's got to be NDISWrapper.

---

