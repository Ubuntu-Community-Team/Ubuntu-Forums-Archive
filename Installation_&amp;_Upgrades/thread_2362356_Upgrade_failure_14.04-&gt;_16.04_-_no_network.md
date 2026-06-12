---
title: "Upgrade failure 14.04-&gt; 16.04 - no network"
date: 2017-05-27
forum: Installation &amp; Upgrades
---

### Post by Christodoulou_Marios on 2017-05-27
Hi, 

i tried to upgrade my xubuntu from 14.04 to 16.04 with sudo apt-get upgrade and it went quite bad. I am writing from my phone, sorry for the format, i cannot paste from my laptop and cannot use the code display feature.


After attempting yo upgrade for ten minutes or so  warning at the terminal said that my installation is likely broken and that to make things work again i should try

 gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache

With sudo i still get access denied. I tried sudo su environment and it does not find the command. 

Desktop displays and applications work. But no network at all. 

The version is still 14.04 it looks like upgrade did not take place.

help :-)

---

### Post by Christodoulou_Marios on 2017-05-27
More info, commanfs were run with sudo in front: 

Ifconfig sees eth0 and lo , says loopback is up and running

Ifup eth0 says interface already configured and quits

Network-admin fails to run gives several glib-object warnings

In /etc/network/interfaces i have

auto lo
iface lo inet loopback

auto eth0 
Iface eth0 inet dhcp

Tried the recovery modes for different kernel versions, no luck.

 Fcsk-check all filesystems runs and does not give warnings.

 Network-Enable networking option fails and gets stuck.

It gives an ifup error, /run/network/ifstate.lo does not exist

---

