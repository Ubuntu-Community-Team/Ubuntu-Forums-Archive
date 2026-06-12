---
title: "Internet acces in linux through windows ?"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by bzren on 2007-05-03
I have a Thomson SpeedTouch 510 v6 ADSL2 modem connected to a Windows PC. And a HP laptop with ubuntu on it, it's connected to the windows machine. Is it possible to get internet access on the laptop ?

---

### Post by bzren on 2007-05-03
Never mind, I figured it out.

192.168.0.1 is the IP address of the win-box and 192.168.0.2 is of the linux-box.

# ifconfig eth1 192.168.0.2 netmask 255.255.255.0
# route add default gw 192.168.0.1 eth1

/etc/resolv.conf:
    nameserver 192.168.0.1
    search mshome.net

And it's done :)

---

### Post by _L_ on 2007-05-07
Hey, do you know how to configure 2 networks ? Like I've got one with Internet acces, and the home network that gets this acces from me... how to configure them ?
Internet Interface: nat0 ; Home network: eth0...

---

