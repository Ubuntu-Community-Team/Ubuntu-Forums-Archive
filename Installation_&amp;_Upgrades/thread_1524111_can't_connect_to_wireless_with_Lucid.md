---
title: "can't connect to wireless with Lucid"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by orengolan on 2010-07-04
After the upgrade to lucid, I can't connect my MacBookPro5,1 to my unencrypted wirless. wired connection works.

I think have the propriety driver because 'sudo jockey-gtk' shows 'Broadcom STA wireless driver'.

wicd-client shows the wireless networks around me but when trying to connect to my network it takes a minute and finaly tells me "Connection Failed: Unable to Get IP Address".
Here is the syslog while wicd is trying to connect:

tail /var/log/syslog

```
Jul  4 21:52:51 oren-laptop dhclient: Listening on LPF/eth1/00:23:6c:97:fc:93
Jul  4 21:52:51 oren-laptop dhclient: Sending on   LPF/eth1/00:23:6c:97:fc:93
Jul  4 21:52:51 oren-laptop dhclient: Sending on   Socket/fallback
Jul  4 21:52:51 oren-laptop dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Jul  4 21:52:51 oren-laptop dhclient: send_packet: Network is unreachable
Jul  4 21:52:51 oren-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Jul  4 21:52:51 oren-laptop avahi-autoipd(eth1)[3735]: Got SIGTERM, quitting.
Jul  4 21:52:51 oren-laptop avahi-autoipd(eth1)[3735]: Callout STOP, address 169.254.9.144 on interface eth1
Jul  4 21:52:51 oren-laptop avahi-daemon[862]: Withdrawing address record for 169.254.9.144 on eth1.
Jul  4 21:52:51 oren-laptop avahi-daemon[862]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.9.144.
Jul  4 21:52:51 oren-laptop avahi-daemon[862]: Interface eth1.IPv4 no longer relevant for mDNS.
Jul  4 21:52:52 oren-laptop avahi-daemon[862]: Withdrawing address record for fe80::223:6cff:fe97:fc93 on eth1.
Jul  4 21:52:52 oren-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jul  4 21:52:52 oren-laptop dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jul  4 21:52:52 oren-laptop dhclient: All rights reserved.
Jul  4 21:52:52 oren-laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul  4 21:52:52 oren-laptop dhclient: 
Jul  4 21:52:52 oren-laptop dhclient: Listening on LPF/eth0/00:25:00:a5:74:62
Jul  4 21:52:52 oren-laptop dhclient: Sending on   LPF/eth0/00:25:00:a5:74:62
Jul  4 21:52:52 oren-laptop dhclient: Sending on   Socket/fallback
Jul  4 21:52:52 oren-laptop dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Jul  4 21:52:52 oren-laptop dhclient: send_packet: Network is unreachable
Jul  4 21:52:52 oren-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Jul  4 21:52:52 oren-laptop avahi-daemon[862]: Withdrawing address record for fe80::225:ff:fea5:7462 on eth0.
Jul  4 21:52:52 oren-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 1)
Jul  4 21:52:52 oren-laptop dhclient: receive_packet failed on eth0: Network is down
Jul  4 21:52:52 oren-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 1)
Jul  4 21:52:52 oren-laptop kernel: [ 2006.861666] forcedeth 0000:00:0a.0: irq 29 for MSI/MSI-X
Jul  4 21:52:53 oren-laptop avahi-daemon[862]: Registering new address record for fe80::223:6cff:fe97:fc93 on eth1.*.
Jul  4 21:52:53 oren-laptop avahi-daemon[862]: Registering new address record for fe80::225:ff:fea5:7462 on eth0.*.
Jul  4 21:53:02 oren-laptop kernel: [ 2016.868034] eth1: no IPv6 routers present
Jul  4 21:53:02 oren-laptop kernel: [ 2016.976052] eth0: no IPv6 routers present
```

sudo iwlist eth1 scan

```
eth1      Scan completed :
          Cell 01 - Address: 00:1B:2F:FD:17:AA
                    ESSID:"prosoa"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-39 dBm  Noise level:-86 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
```





ifconfig 

```
eth0      Link encap:Ethernet  HWaddr 00:25:00:a5:74:62  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:ff:fea5:7462/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:304165 (304.1 KB)  TX bytes:186605 (186.6 KB)
          Interrupt:29 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:23:6c:97:fc:93  
          inet6 addr: fe80::223:6cff:fe97:fc93/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:3915
          TX packets:0 errors:59 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:944 (944.0 B)  TX bytes:944 (944.0 B)
```



iwconfig 

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:170
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

vboxnet0  no wireless extensions.
```




sudo dhclient eth1

```
There is already a pid file /var/run/dhclient.pid with pid 3891
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:23:6c:97:fc:93
Sending on   LPF/eth1/00:23:6c:97:fc:93
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.2.35
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

---

