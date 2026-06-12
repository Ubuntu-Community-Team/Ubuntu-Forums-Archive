---
title: "configuring fixed IP"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by pdpi on 2005-11-14
I just assembled my first server (yay!), for experimental use, web development, the works. For obvious reasons, I'd like the machine to have a fixed IP within my home network. I'm behind a Linksys router, for what it's worth.
I figure any configurations should go into /etc/network/interfaces, but my single attempt thus far has required me to grab a screen and keyboard and cross the house to recover from it (the server's headless), and I'd much appreciate not have to do that again...

So, could anyone please give me a hand?

---

### Post by salva on 2005-11-14
I'm not sure of the command line way to do this, but the way i did it way thru the gnome-network tool - and it seems to get it right...
if it can help heres the content from my interfaces file:
```
# The primary network interface
iface eth0 inet static
address 10.0.0.2
netmask 255.0.0.0
gateway 10.0.0.1
```

as far as i remember from when i did it manually the static bit is the main mover, and the rest should be self explainable :)
Hope it helps

---

### Post by matthew on 2005-11-14
Look in /etc/network/interfaces
That is the file that determines how your IP is set and what it will be as well as your primary network interface (i.e. eth0, etc)

Here is a sample for a static IP to get you going. I recommend you man interfaces to learn more.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
    script grep
    map eth1

# The primary network interface

iface eth0 inet static
address 192.168.2.102 #this is what you set for your home network
netmask 255.255.255.0 #this is pretty standard
gateway 68.2.16.30 #this comes from your internet provider and can be found in your router's setup somewhere

auto eth0

```

---

### Post by pdpi on 2005-11-14
Well, I take RTFM as my mantra. but in this particular case, 'man interfaces' was somewhat incomprehensible.

Either way, I tried your suggestion, to no avail (and one more trip to the headless server)

---

