---
title: "Upgrading server edition"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Dagur on 2006-06-01
Will changing sources.list, apt-get update, apt-get dist-upgrade work for Ubuntu 5.10 server?

---

### Post by ubuntu_demon on 2006-06-01
There should be no problem as far as I know. But I don't know what packages else then ubuntu-base and linux-server are installed by 6.06 server.

First change all references to breezy to dapper in /etc/apt/sources.list
$sudo pico /etc/apt/sources.list

Then do the actual upgrade by :

$sudo apt-get update
$sudo apt-get dist-upgrade

make sure ubuntu-base is installed :
$sudo apt-get install ubuntu-base

make sure the server kernel is installed :
$sudo apt-get install linux-server
or : $ sudo apt-get install linux-server-bigiron (if you have such a server)

here's some information regarding upgrading :
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

---

### Post by Dagur on 2006-06-01
thanks a bunch! :KS :KS :KS

---

### Post by ubuntu_demon on 2006-06-01
[QUOTE=Dagur]thanks a bunch! :KS :KS :KS[/QUOTE]
No problem. 

If there are any problems let us know and post your sources.list.

---

