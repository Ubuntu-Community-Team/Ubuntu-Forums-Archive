---
title: "Intel Built-in Network Card not working??"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by muhammadzeeshan on 2010-10-10
Hi,
I am new to UBUNTU. I have installed UBUNTU 9.04(Jaunty). After installation i found that network card is not wokring. And id doest not list in "System > Preferenes > Network Connections" So , i got another card from my friend and try to search on internat about my problem but still cant find solution.
Some commands output is here which may be help to solve problem

```

root@mzeeshan-desktop:/home/mzeeshan# uname -r
2.6.28-11-generic
root@mzeeshan-desktop:/home/mzeeshan# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:44:4a:45:12  
          inet addr:192.168.5.37  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::202:44ff:fe4a:4512/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3774 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4307045 (4.3 MB)  TX bytes:583067 (583.0 KB)
          Interrupt:22 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 5e:25:17:a1:18:ac  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@mzeeshan-desktop:/home/mzeeshan# lspci
00:00.0 Host bridge: Intel Corporation Device 0069 (rev 12)
00:01.0 PCI bridge: Intel Corporation Auburndale/Havendale PCI Express x16 Root Port (rev 12)
00:19.0 Ethernet controller: Intel Corporation Device 10f0 (rev 05)
00:1a.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 5 (rev 05)
00:1c.6 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 7 (rev 05)
00:1c.7 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Ibex Peak LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation Ibex Peak 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Ibex Peak SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation Ibex Peak 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
06:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
06:00.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
root@mzeeshan-desktop:/home/mzeeshan# 

```


I don't know what to do next. Any help will be greatly appreciated..
Thanks

---

### Post by mikewhatever on 2010-10-10
The output you posted shows an IP address, which means the network card works, at least a little. What's the problem exactly, or why do you think it doesn't work?

---

### Post by muhammadzeeshan on 2010-10-10
"eth0" is the network card which is temporary. When i install Ubuntu i saw only two reading in result if this command "ifconfig -a". The output is 



lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr 5e:25:17:a1:18:ac  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


The problem i found is that it doesnt work because it does not listed in System > Preferenes > Network Connections".

---

### Post by mikewhatever on 2010-10-10
So what's the model of the non-working network card?
Can you put it back in and post the output of the following command:

lspci | grep -i net

---

### Post by muhammadzeeshan on 2010-10-10
```

root@mzeeshan-desktop:/home/mzeeshan# lspci | grep -i net
00:19.0 Ethernet controller: Intel Corporation Device 10f0 (rev 05)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
root@mzeeshan-desktop:/home/mzeeshan# 

```

---

### Post by muhammadzeeshan on 2010-10-10
It's this becuase second one is of Realtek and it is temporary card. I am sure.
00:19.0 Ethernet controller: Intel Corporation Device 10f0 (rev 05)

---

### Post by mikewhatever on 2010-10-10
Yeah, that device is not recognized at all. Did it work on other versions of Ubuntu? If you have Windows installed in that computer, check its device manager.

---

### Post by muhammadzeeshan on 2010-10-11
I was using Windows XP and this device was working perfect. Its not working on Ubuntu. Is there any solution ?

---

### Post by Hentavir on 2010-10-11
I think your network card is not supported in 9.04,
try a newer version, 10.10 or 10.04

---

