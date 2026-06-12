---
title: "No network interfaces detected"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Jack Thomson on 2007-11-11
Hi,

I'm new to Ubuntu and am having problem installing Ubuntu Server 7.10.

When I install it I get the following error 

> 
No network interfaces detected

No network interfaces were found. The installation system was unable to find a network device.

You may need to load a specific module for your network card, if you have one. For this, go back to the network hardware detection step.


**However** when I boot up using Ubuntu Desktop 7.10 then the network is fine.

So obviously Desktop is installing something that Server isn't but what is it ?

Other bits of info are

[LIST]
[*]If I type 'lshw' on the Server edition then the ethernet is found but it is disabled.
[*]My motherboard is a 'Asustek S775 Intel 945G MATX Audio Lan Graphics'.
[/LIST]

Can anyone help ?

---

### Post by Jack Thomson on 2007-11-17
Well I managed to get this to work.

I simply went to /etc/network and added the lines below to *interfaces*

```
# The primary network interface
auto eth0
iface eth0 inet dhcp

```

And it all works nicely now...

---

