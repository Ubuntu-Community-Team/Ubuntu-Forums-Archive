---
title: "unmanaged network device not properly loaded"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by bkleine on 2011-11-01
Hi,

I have a ethernet Intel e100 NIC which has worked for years and still runs well. In our home LAN we have fixed internet adresses. In debian and ubuntu I had installed this card without any problems once the correct entries were fixed in /etc/network/interface:

auto eth0
iface eth0 inet static
	address 192.168.1.201
	netmask 255.255.255.0
	broadcast 192.168.1.255
	gateway 192.168.1.199
	dns-nameservers 192.168.1.199

During booting in Ubuntu 11.10 this card is not loaded due to an error in the installation script: the directory /run/network is not created. 

For this reason I can boot and after the desktop is ready I can run the following:

as admin: 
ifdown eth0
mkdir /run/network
ifup eth0

after that the card works e.g. to reach this forum. It is obvious that the script which wants to start the card does not check for the existence of the directory and stops executing. It should check whether the dir exists and if not create it!!!

Alternatively, I would like to get help to get this card managed by the network manager. I never tried that.

Greeting from the Black Forest

Bernhard

---

### Post by cbowman57 on 2011-11-01
Edit **/etc/NetworkManager/NetworkManager.conf** change managed=false to **managed=true**

---

### Post by bkleine on 2011-11-03
thanks for your tip, that helped with managing. However the real problem, the lack of directory generation, has not been settled. 

ANY HELP WELCOME!

Bernhard

---

