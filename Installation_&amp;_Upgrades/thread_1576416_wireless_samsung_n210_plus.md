---
title: "wireless samsung n210 plus"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by pilouchette on 2010-09-17
Hello ):P

I've made the choice to install ubuntu 10.04 on my samsung n210 plus netbook

I know there is a ubuntu netbook version but I prefer the original version of ubuntu 10.04 ;)

The problem is that the wireless doesn't work, I had a look on the forum and find solution only for ubuntu netbook version and I actually didn't understand anything :(

I've downloaded the driver hybrid-portsrc-x86_32-v5.60.48.36 and my version of ubuntu is 32 bit.

As it's says on the readme file, I've checked it I had the kernel package by entering this command;
ls /lib/modules/`uname -r`/build
but it says;
no such file or directory

I was not sure about the 'uname', should I replace it by the name of the package or something ???

Thank you so much for helping me :D

---

### Post by pilouchette on 2010-09-17
hey ;)

I entered the command;

lspci -nn | grep Network
sudo lshw -C network
as I found it in an other thread but didn't find the same so can not follow the same instruction.
What I found;

  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:24:54:a9:69:d0
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f0200000-f0203fff ioport:2000(size=256)

Hope that will help :)

---

### Post by pilouchette on 2010-09-17
:confused: It's seems that I am in an ubuntu 64 bit !!! Do you think I should reinstall it as a 32 bit ???

---

### Post by pilouchette on 2010-09-17
I now entered the command

sudo apt-get install linux-headers-`uname -r` build-essential

 and this is what I found;

Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
linux-headers-2.6.32-24-generic est déjà la plus récente version disponible.
linux-headers-2.6.32-24-generic passé en « installé manuellement ».
E: Impossible de trouver le paquet build-essential

Now I am stuck :(

---

### Post by pilouchette on 2010-10-05
Still no answer :s

I am stuck :((

Any body can help? :))

---

### Post by Peter09 on 2010-10-05
Have you updated your system using the hard wired link. You need to do that so that any drivers that are available will be downloaded. Then check the System->Admin->Hardware to see if any driver needs enabling.

---

