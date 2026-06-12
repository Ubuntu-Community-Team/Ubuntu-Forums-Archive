---
title: "Unable to connect to the Internet ( HTTP )"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by stormac on 2006-12-18
Hi Linux Guru(s),

I am new to Ubuntu (linux), I did install Ubuntu 6.06 to my machine, 512MB. 80Gigs, AthonXP, ASUS A7N8x motherboard.  Network, sound and video are all on-board by ViaCom.

I tried reading through the posts but, there's so much to go through and I've spent a good 3 hours reading through and I can't find an answer.

So here it is my share of a problem ...

I was able to install with no issues. My problem is, I am not able to connect to the Internet using Cable Internet via modem (Motorolla, provided), using RJ-45.  My default connection set-up is DHCP using the Network (manager).  I configured Firefox to Directly Connect to the Internet. I am not able to browse the Internet nor get some of the chat features (to check internet connection) to work. :confused: 

I do hope anyone with good knowledge can share how to resolve this issue.

Thank you in advance!

---

### Post by dbott67 on 2006-12-18
Hopefully, you can copy & paste the output of the commands below to a text file & save it to USB/floppy and bring it over to a working computer.

I'll also need to know your network setup (are you using a router, such as D-Link, Netgear or Linksys, etc.).

Can you please post the output of the following commands:

```
cat /etc/network/interfaces 
```

Here's mine as an example:

```
dbott@dapper:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```

This command shows ALL network interfaces on the system (whether enabled or not):

```
ifconfig -a
```

```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

This command outputs the network hardware detected:

```
sudo lshw -C network
```

Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

And finally:
```
route -n
```
This shows the default route off of your network.

---

