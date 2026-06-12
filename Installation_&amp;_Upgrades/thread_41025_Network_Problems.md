---
title: "Network Problems"
date: 2005-06-11
forum: Installation &amp; Upgrades
---

### Post by parradux on 2005-06-11
During the installation of Ubuntu I couldnt configure my network no matter what I tried. I tried disabling WEP, enabling it, tried configuring manually and it still wouldnt work. 

I need to know how to fix this, in order to get internet on my ASUS M6Bne Laptop.

My router in D-Link D-624. 

How would I go along configuring my network?

---

### Post by xtrm on 2005-06-11
could u post your /etc/network/interface or an ifconfig output ? 
check also your /etc/resolv.conf

---

### Post by parradux on 2005-06-12
[QUOTE=parradux]During the installation of Ubuntu I couldnt configure my network no matter what I tried. I tried disabling WEP, enabling it, tried configuring manually and it still wouldnt work. 

I need to know how to fix this, in order to get internet on my ASUS M6Bne Laptop.

My router in D-Link D-624. 

How would I go along configuring my network?[/QUOTE]
 fconfig yields:

lo Lin encap: Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTI:16436 Metrick:1
RX PACKETS:729 ERRORS:0 DROPPED:0 OVERRUNS:0 FRAME:0
TX PACKETS:729 ERRORS:0 DROPPED:0 OVERRUNS:0 CARRIER:0
collisions:0 txqueuelen:0
RX bytes:64801 (63.2 KiB) TX bytes:64801 (63.2 KiB)


iwconfig yields:

lo no wireless extensions

eth0 no wireless extensions

eth1 unassociated ESSID:off/any
Mode: Managed Channel=0 Access Point: 00:00:00:00:00:00
Bit Rate=0 kb/s Tx Power = 20dBm
RTs thr:off Fragment thr:off
Power Management:off
Link Quality:- Signa Level:0 Noise Level:0
Rx invalid nwid:0 Rx invalid crypt:- Rx Invalid frag:0
Tx Excesssive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions

/etc/resolv.conf doesnt exist. 

/etc/network/interace gives me 

auto lo
iface lo inet loopback 

mapping hotplug
              script grep
              map eth1

---

### Post by parradux on 2005-06-12
bump...

---

### Post by kleeman on 2005-06-12
What output do you get from

sudo iwlist eth1 scanning

Assuming your router essid is MYNET (iwlist above should show what it is)
then do
sudo iwconfig eth1 essid MYNET

and then

sudo dhclient eth1

---

### Post by parradux on 2005-06-12
[QUOTE=kleeman]What output do you get from

sudo iwlist eth1 scanning

Assuming your router essid is MYNET (iwlist above should show what it is)
then do
sudo iwconfig eth1 essid MYNET

and then

sudo dhclient eth1[/QUOTE]
 Thanks I got it working.

I have one problem just now, every single time I reboot, I have to re-enter all my info. Is there a way I can automate this process?

---

