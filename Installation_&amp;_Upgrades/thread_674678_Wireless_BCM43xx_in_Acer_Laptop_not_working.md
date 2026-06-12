---
title: "Wireless BCM43xx in Acer Laptop not working"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by paiarunk on 2008-01-21
Hai

I am trying to enable wireless network in my acer laptop BCM94311MCG wlan mini-PCI (rev 01) on my laptop with Ubuntu 7.10 Gusty , I am seeing that the wireless routers are been detected using iwlist scan command, but the eth1 is not able to connect to router

My router has WPA ascii password, please help

arun@arun-laptop:~$ lspci
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
arun@arun-laptop:~$ modprobe bcm43xx
arun@arun-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:72:00:6F:1E  
          inet addr:192.168.50.246  Bcast:192.168.50.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe00:6f1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8126 errors:0 dropped:0 overruns:0 frame:1
          TX packets:4874 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4580168 (4.3 MB)  TX bytes:1015654 (991.8 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1D:D9:3D:82:17  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:847 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:546 (546.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9248 (9.0 KB)  TX bytes:9248 (9.0 KB)

arun@arun-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

arun@arun-laptop:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:16:01:8D:83:21
                    ESSID:"ashraya"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-64 dBm  Noise level=-66 dBm
                    Extra: Last beacon: 48ms ago

arun@arun-laptop:~$

---

### Post by linuxbrit on 2008-01-23
Not sure if the wireless card will work, as there are no Linux drivers for it? I did manage to use ndiswrapper and the windows XP driver though - is this the problem I wonder?

:)

---

