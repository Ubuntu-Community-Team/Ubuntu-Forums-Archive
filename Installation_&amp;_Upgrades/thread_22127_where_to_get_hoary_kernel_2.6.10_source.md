---
title: "where to get hoary kernel 2.6.10 source ?"
date: 2005-03-25
forum: Installation &amp; Upgrades
---

### Post by dukeinlondon on 2005-03-25
Just installed kubuntu and it's running kernel 2.6.10 but I need the sources to get compile the driver for my wireless pci card edimax ed-7128g (ralink chipset). I've found the package list for hoary but it does not include that version of the kernel source .... Can I take any debian kernel source ?

---

### Post by az on 2005-03-25
install build-essential and linux-source-2.6

Just install the linux-headers -  that is much easier.  Otherwise, you have to configure the kernel and everything...

apt-cache search linux-headers-2.6

---

### Post by Dracontopes on 2005-03-26
Or you can use synaptic and search for **linux-source** and/or **linux-headers**. 

Good luck!

---

