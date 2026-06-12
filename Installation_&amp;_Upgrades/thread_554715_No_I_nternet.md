---
title: "No I nternet"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by deroldj on 2007-09-19
can not get internet to work. Works well with windows and puppy (same machine). I have a nettopia router type modem connected to dsl through ethernet. networking set to dhcp
Ubuntu says I have a network connection   interface wired ETH0, speed 100ml/s, driver 8139too
I can not get on internet

I ran     pppoeconf     and got
  found eth0 and etoavah
  access concentrator of your provider did not respond
checked et0 and setup to dhcp, checked eth0avah, and said connection not found

I ran   /etc/network/interfaces     and got
  auto lo
  iface lo inet loopback

  auto eth0
 iface eth0 inet dhcp

  auto eth1
  iface et1 inet dhcp

  auto eth2
  iface eth2 inet dhcp

  auto ath0
  iface ath0 inet dhcp

  auto wlan
  iface wlan inet dhcp

I tried adding addres and netmask with sudo gedit, but did not help, also tried * or lines eth1, eth2, ath0 and wlan, but did not help

I have an address for my access concentrater, if that is what is neede, but dont know where to stick it  :lolflag:

---

### Post by deroldj on 2007-09-19
can this problem be solved?

---

