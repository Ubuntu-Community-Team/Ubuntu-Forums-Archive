---
title: "Easy route to reinstallation"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by nickmcg on 2006-10-30
In the hope that this might be of use, I've condensed the routine operations I need to perform after reinstalling (I've done this a lot, because I keep playing with things I don't understand & need to clean up the mess I've made)

Partitioning:
keep /home in its own partition - makes it much easier to reinstall! Make sure you remember which partition to mount as /home

Upgrade - Dapper to Efty:
rausb0 fails to initialise from the gui - need to use 
sudo ifconfig rausb0 up
sudo iwconfig rausb0 essid networkname key wepkey
 -  I don't know if this problem is mine alone

If you want, enable the extra repositories:
gksudo gedit /etc/apt/sources.list - remove the '#' from lines beginning '# deb'

network:
if, like me, you have a mixed network, life is made much easier by the addition of samba and winbind (either sudo apt-get install or synaptic - both work equally well), and modifying the file /etc/nsswitch.conf, changing the hosts line to include 'wins'
e.g hosts:          files wins dns

This gets my system into a working state with the minimum stress, an I hope it may help others.

Cheers

Nick

---

