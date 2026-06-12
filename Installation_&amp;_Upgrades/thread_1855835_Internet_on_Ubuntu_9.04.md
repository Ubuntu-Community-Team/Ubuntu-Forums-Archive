---
title: "Internet on Ubuntu 9.04"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by iUbuntu on 2011-10-07
Hi, 

I have installed Ubuntu 9.04 [thats the version I have and I dont have media to dowonload 11.04 and install on other machine for now.. I am hoping once I go online on 9.04 I can upgrade to 11.04]. 

I am unable to connect to the internet using a direct wired connection to my modem. I have the eth0 box checked. 

Can someone please help me to get online. 

Thanks

---

### Post by dino99 on 2011-10-07
you may find what you need here:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

and welcome on the forum :)

---

### Post by iUbuntu on 2011-10-07
Thnx dino99. 

I am not looking to share a connection with other computer.

All I want is to get my laptop online which is connected to the modem

---

### Post by mörgæs on 2011-10-07
Upgrading all the way means four upgrades. If you manage (this is a risky proces) you will end with Grub1 on ext3. 

If you rather want Grub2 and ext4, it is much easier to begin with a fresh install. You can buy a 11.04 disk at a very low price online.

---

### Post by coffeecat on 2011-10-07
I agree with mörgæs. There is also another problem with upgrading from 9.04 all the way to 11.04. 9.04 is unsupported and you have to use the old-releases repository. See:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

But it gets worse. You cannot upgrade directly from 9.04 to 10.04, you have to go via 9.10, and 9.10 is now also unsupported. Because of this the routine way of upgrading 9.04 to 9.10 will not work and you have to use the alternate CD method:

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

Which brings you back to the problem of media again. There is (or was - I don't know if it will still work) a way of getting around this by tricking the system into thinking 9.10 is still supported. I can post a link for this method if you want, but you would still be better off getting hold of a 11.04 CD, imo.

---

### Post by iUbuntu on 2011-10-08
thnx for the replies. 

I have done a fresh installation to 10.04 I still am not able to connect to a wired internet connection. 

It is so sad that there is no out of box support for internet on such a good OS :(. 

Any suggestions ? [I dont have access to latest ubuntu for now, so 10.04 is all I have to work with ]

Thanks again !

---

### Post by coffeecat on 2011-10-08
> **iUbuntu said:**
> It is so sad that there is no out of box support for internet on such a good OS :(. 

In fact it is extremely rare not to have out of the box support for ethernet in Ubuntu. If you are not getting this, it needs investigating. Post the terminal output of these commands:

```
lspci | grep -i ethernet
sudo lshw -C network
ifconfig
```

---

### Post by iUbuntu on 2011-10-09
Hello coffee cat, 

Thanks for helping me out. 

Here is the info you requested:


$ sudo lshw -C network

  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:5b:b5:2e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d1100000-d110ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:ce:62:c6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:2000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d102ffff(prefetchable)


$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:ce:62:c6  
          inet6 addr: fe80::21e:68ff:fece:62c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:235274 (235.2 KB)  TX bytes:5382 (5.3 KB)
          Interrupt:28 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77568 (77.5 KB)  TX bytes:77568 (77.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:69:5b:b5:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


$ lspci | grep -i ethernet
08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Look forward to your reply . Thanks again !

---

### Post by coffeecat on 2011-10-09
That Realtek ethernet device *should* work out of the box for you, but it hasn't been assigned an IP by your router. I suggest you look at your modem-router settings and try a different ethernet cable in case it is faulty. Also - if you click on the network manager icon you should see something like "Auto eth0". Click on "connect". Does anything happen?

---

### Post by speedwlk on 2011-10-09
Forgive me for asking, but did you set up the internet connection? 

Please have a look at

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

---

### Post by iUbuntu on 2011-10-11
I finally installed 11.04 after all the failed attempts. 

The internet connected once after the installation and then went silent again :(

I can see the "link" light on modem green when I connect to my different windows7 machine while it blinks orange on this one
[So the ethernet cable is working fine]

clicking on eht0 does not help, it shows a little animation and does not connect or tell what was wrong. 

Using sudo pppoeconf did not help either. I end up with message:
"Sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem."

How do I get this sorted :(

Can someone please point to specific instructions incase you provide a link

Thanks for the help !

---

### Post by iUbuntu on 2011-10-11
I finally installed 11.04 after all the failed attempts. 

The internet connected once after the installation and then went silent again 

I can see the "link" light on modem green when I connect to my different windows7 machine while it blinks orange on this one
[So the ethernet cable is working fine]

clicking on eht0 does not help, it shows a little animation and does not connect or tell what was wrong. 

Using sudo pppoeconf did not help either. I end up with message:
"Sorry, I scanned 2 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem."

How do I get this sorted 

Can someone please point to specific instructions incase you provide a link

Thanks for the help !

---

