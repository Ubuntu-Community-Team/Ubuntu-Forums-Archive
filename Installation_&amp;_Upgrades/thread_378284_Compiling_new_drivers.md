---
title: "Compiling new drivers"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by GeertPoels on 2007-03-07
Hello,

I've got an ASUS P5B-E Plus motherboard which holds a Marvell Gigabit LAN controller.
The Linux driver sources (with 2.4 and 2.6) is downloadable from the Asus support site.

Apart from that NIC, I also got a Belkin Wireless G+ MIMO USB controller.(type F5D9050).
Though Belkin doesn't support Linux, I found out that this controller features a Ralink chip 2501/2601.
Ralink has a driver. (btw on [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) you can find drivers for older versions)


The Belkin driver can be added as a module, the network card driver has to be applied as a kernel patch.

By default, Ubuntu doesn't come with the kernel sources so I downloaded them through Synaptic.
Synaptic indicated that I downloaded the kernel sources + Ubuntu patches.
I found the sources afterwards zipped in a single file in /usr/src.
This folder already contained some folders : generic headers for the currently provided kernel.
Oddly enough, the sources didn't have this 'generic' in their name.

Some questions :
Do I have the sources corresponding to my current kernelversion or did I obtain the latest sources ?
What's the best way to recompile the kernel, holding the same default options ?
Maybe somebody else might hold this same hardware, how can these drivers become part of the distribution ?

Thanks,

Geert

---

### Post by pay on 2007-03-07
Here's [howto](http://www.howtoforge.com/kernel_compilation_ubuntu) compile the kernel. The drivers will probably only be added if their is enough demand and they have a non restrictive license.

---

