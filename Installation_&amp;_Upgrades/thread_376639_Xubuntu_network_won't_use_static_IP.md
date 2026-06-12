---
title: "Xubuntu network won't use static IP"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by xadder on 2007-03-05
I just did a clean install of Xubuntu edgy on an IBM Thinkpad T43  (after the upgrade from dapper failed miserably). The install went fine, but I am having problems with the network. I have set a static IP, but xubuntu keeps switching to look for DHCP stuff. I have been doing
/etc/init.d/networking restart to get things going occassionally, but success seems random
(I managed to grab all updates during a good spell though - so there is nothing wrong with the static-IP setup when it wokrs).

How can I make xubuntu stiop looking for DHCP?

Thanks.

---

### Post by ffxr on 2007-03-05
where are you configuring your network?

can u post the contents of 

```
 gksu mousepad /etc/network/interfaces 
```

---

### Post by xadder on 2007-03-05
The problems I was/am having were from my office, which has a default DHCP (password-protected system) system but where I have to use static IP to access certain computers. 

I'm home now and my home broadband worked great - probably as it uses DHCP anyway. Unfortunately I won't be back in the office until wednesday to continue with the problem-fixing there, but  here's the output you requested (minus the real IP):

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 129.16.35.151
netmask 255.255.0.0
gateway 129.16.35.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
auto lo
iface lo inet loopback


iface eth0 inet dhcp
address xxx.xx.xx.xxxx
netmask 255.255.0.0
gateway xxx.xx.xx.x

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

auto eth0

```

This was taken while I have home-broadband. I don't know if it looks different from the office.
I don't know what the eth1 eth2 bits are for. I have just one ethernet output, which I thought was 
eth0. I have one wireless too, but that isn't configured. By the way, I have a stationary computer too which is running great. That was installed as ubuntu-desktop though, with aptitude install xubuntu-desktop for fun. No problems. The problem machine was the ibm T43, which had the xubuntu installed from the .iso, if that makes a difference.

Any tips appreciated, and I'll test them on wednesday.

Thanks

---

### Post by cookfromfrozen on 2007-03-05
See this line:

```
iface eth0 inet **dhcp**
```

You need to change it to "**static**", so it looks like this:

```

iface eth0 inet static
address 129.16.35.151
netmask 255.255.0.0
gateway 129.16.35.1
```

Restart your network interfaces with

```
sudo /etc/init.d/networking restart
```

and all should be well, provided your IP, netmask and gateway settings are correct.

---

### Post by xadder on 2007-03-07
Still problems, but maybe solved. Back in the office I used system - networking and switched to static IP. This gave an interfaces file with "static" exactly as you suggested. But when I do a network restart I get:

> sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 8467
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:e0:ec:d7
Sending on   LPF/eth1/00:0e:35:e0:ec:d7
Sending on   Socket/fallback
DHCPRELEASE on eth1 to xxx.xx.x.xxx port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:e0:ec:d7
Sending on   LPF/eth1/00:0e:35:e0:ec:d7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPOFFER from xxx.xx.x.xxx
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from xxx.xx.x.xxx
bound to xxx.xx.x.xxx32 -- renewal in 397 seconds.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


( changed the numbers to xxxx for security)


I have just got it working with an explicit ifconfig eth0, which I can live with for now (if it keeps working anyway!). 

I saw another post after googling for the ubuntu + SIOCSIFADDR error above [HTML]http://ubuntuforums.org/showthread.php?t=221768[/HTML] with other solutions that I can try if needed. Still, seems strange that something so basic causes problems. 
Worked perfectly first time with dapper.

---

### Post by xadder on 2007-03-07
Small update. Just doing ifconfig eth0 stopped working.  Now I am running again, but only after hand-editing /etc/iftab and /etc/network/interfaces and simply commenting out all non-eth0 entries.

Puzzling.....

---

