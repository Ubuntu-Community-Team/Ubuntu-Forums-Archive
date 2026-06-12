---
title: "[SOLVED] Atheros AR5212/5213 wireless card"
date: 2008-07-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chrismine on 2008-07-30
I have a wireless PCI card with the above chip set. It use to work fine in Hardy. Since I installed Intrepid it does not work anymore.  Device Manager shows the card as detected, but it seems that the drivers is not loaded.  As far as I can ascertain I have the necessary linux-restricted modules installed.  The card is listed in lspci as: 00:0a.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01) and ifconfig shows: chrisjan@ubuntu:~$ ifconfig eth0      Link encap:Ethernet  HWaddr 00:0a:48:1b:08:c8             inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0           inet6 addr: fe80::20a:48ff:fe1b:8c8/64 Scope:Link           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:14895 errors:0 dropped:0 overruns:0 frame:0           TX packets:14807 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:9337468 (9.3 MB)  TX bytes:2329753 (2.3 MB)           Interrupt:23 Base address:0x6000   lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr: ::1/128 Scope:Host           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:18161 errors:0 dropped:0 overruns:0 frame:0           TX packets:18161 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:919119 (919.1 KB)  TX bytes:919119 (919.1 KB)   Is there anybody with the same problem?  Thanks.   Sorry for the way the post looks but it seems that I am too stupid to get the formatting right - can somebody please enlighten me as to the settings and meaning of the thread tools?

---

### Post by roadkilla on 2008-07-30
you need to enable Atheros restricted HAL in
**System->Administration->Hardware Drivers**
and also blacklist ath5k the open source driver which doesn't yet support all chipsets.
to disable the open source driver add this **blacklist ath5k** to **/etc/modprobe.d/blacklist**
if you don't know what you need you can post your **lsmod | grep ath**
and I'll help you a bit.

---

### Post by autocrosser on 2008-07-30
Hmmmm--I use a D-Link card that is the AR5212/AR5213 chipset & have had no problems with it--you should know that as of the-3 kernel the interface name has changed to wlan0--ath0 is no longer used. As soon as I made the change, my card worked normally.

My lspci reports:
Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

Before you blacklist anything---check ifconfig wlan0. Mine looks like:

wlan0     Link encap:Ethernet  HWaddr 00:11:95:93:d4:81  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe93:d481/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8690421 (8.6 MB)  TX bytes:3551214 (3.5 MB)

---

### Post by chrismine on 2008-07-31
Thanks roadkilla - Atheros restricted HAL does not show up in Hardware Drivers.

Ok I blacklisted the driver and rebooted. Still does not show.

lsmod shows nothing for ath0 or wlan0

Some time ago the wlan0 interface did show up, I checked from time to time after downloading updates. Now nothing shows.

Thanks.

---

### Post by chrismine on 2008-07-31
Thanks autocrosser - i am running the -5 kernel. At some stage jockey were broken but even after it was fixed and showed me the NVIDIA drivers the Atheros HAL never showed up like in Hardy. 

This card has never worked since I installed Intrepid from scratch.

Thanks.

---

### Post by chrismine on 2008-08-14
About two days ago I downloaded three updates:
Upgraded the following packages:
gnome-session (2.23.6-0ubuntu1) to 2.23.6-0ubuntu2
libnss3-1d (3.12.0.3-0ubuntu4) to 3.12.0.3-0ubuntu5
module-init-tools (3.3-pre11-4ubuntu8) to 3.3-pre11-4ubuntu9

It asked me to install the package mainters version of /etc/modbrobe.d/blacklist and after rebooting my wireless card started working. I assume it were the module-init-tools package that fixed it.

 I then only had to input the SSID and WEP key and I was up and running.

---

