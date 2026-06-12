---
title: "openbox wireless"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by guy.tarded on 2010-11-17
hi folks,

I'm pretty new to linux so here I am asking some questions to you all.
I'm looking to enable my wireless connection on my inspiron 1100 running ubuntu 10.10 with openbox and slim.

1. when id do " lshw -C network" the output says*-network DISABLED etc..
How does this come? There's no wireless button on the computer and using the FN -F2 button doesn't make any change either. 

My wireless device is running with the ath5k driver and is listed well in iwconfig. Where do I have to start looking to enable the bloody networkcard.

2. I started my ubuntu experience from base install, what are the exact packages that i need for running wpa2 encrypted wireless networks?
What is also a very lightweight graphical network manager that doesn't depend on gnome or kde? I want to keep my openbox as simple as it is :)

Thanx in advance!!!!

---

### Post by cchhrriiss121212 on 2010-11-17
I'd go for wicd, but gnome-network-manager doesn't actually bring in that much gnome stuff. You might be interested in looking at [crunchbang]("http://crunchbanglinux.org/") which is very similar to what you have set up.

---

### Post by guy.tarded on 2010-11-17
hi, a found some other old topic where you spoke about x fixes. Where can i find them?

---

### Post by guy.tarded on 2010-11-19
problem solved by editing /etc/network/interfaces

i added:

auto wlan0
iface wlan0 inet dhcp

Posting my solution just in case anybody will have the same problem.

---

