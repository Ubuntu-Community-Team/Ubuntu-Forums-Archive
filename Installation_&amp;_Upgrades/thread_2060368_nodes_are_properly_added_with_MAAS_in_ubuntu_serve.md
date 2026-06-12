---
title: "nodes are properly added with MAAS in ubuntu server 12.04"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by dlakshmi on 2012-09-20
I am trying to install ubuntu server 12.04 LTS for Cloud. I have installed MAAS server in one system. In my server I have edited "/etc/network/interfaces" as follows:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
     address 117.***.***.***
     netmask 255.255.255.240
     network
      broadcast
       gateway
       dns-nameserver 
       dns-search ubuntukit.com

auto eth0:0
iface eth0 inet static
       address 172.***.***.***
       netmask
      gateway

  In this file, we planed to connect ubuntu repository through eth0(public IP) and to connect node with server through eth0:0 (private IP).
       While I try to connect node by installing MAAS, I got my MAAS IP and port address. I have connected. But When I open "172.16.1.131/MAAS" it shows " 0 nodes are connected. plz help me to solve this error.

---

