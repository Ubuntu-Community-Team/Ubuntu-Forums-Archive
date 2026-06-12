---
title: "Dual network cards trouble"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by bedaone on 2005-05-30
I have a notebook with one wlan card and one ordenary eth card. I want to use the wlan card for internet connection and the eth card for sharing the connection with another computer.
The wlan works ok when i have disabled the eth-card, but as soon as i activate it, i am no longer able to connect to internet via the wlan-card. My guess is that ubuntu prefers the wired card somehow, but i cant find any way to change this. The wlan-card is using DHCP and i've configured the eth card with 192.168.0.1.

Does anyone know what settings i have to change to get this to work?

---

### Post by Mez on 2005-05-30
[http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/)

That should give you some good info on how to set your PC up as a"router"

---

### Post by bedaone on 2005-05-30
Ok, thats a good guide, but it doesnt solve my primary problem. Thing is that i cant even activate both network devices at the same time. If i do, ubuntu tries to use the wrong interface to connect to the net (at least i think thats what happens), and thus i cant connect from either of the computers. Annoying to say the least.

I've looked at the route command as well as the /etc/network/interfaces file, but i didn't understand much of it...

---

