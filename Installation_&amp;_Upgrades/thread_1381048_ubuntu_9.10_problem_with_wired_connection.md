---
title: "ubuntu 9.10 problem with wired connection"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by new_to_ubun2 on 2010-01-14
The problem is network manager on top shows connection is established but I cannot browse internet, output for ping [www.google.com](www.google.com) is unknown host
please need urgent help with this.
thanking in advance.

---

### Post by Ilalmi on 2010-01-14
Have you set the gateway and dns-server?

---

### Post by new_to_ubun2 on 2010-01-15
> **Ilalmi said:**
> Have you set the gateway and dns-server?
Yes, I've simply added new wired connection through network manager by filling up IPv4 settings manually.

---

### Post by new_to_ubun2 on 2010-01-15
Also ```
sudo pppoeconf
``` don't work for me :(

---

### Post by abrrymnvette on 2010-01-15
Are your interfaces up? If you type ifconfig in a command prompt what comes back? 

For some reason mine wouldn't come back up after updates. Reboot fixed it.

---

### Post by new_to_ubun2 on 2010-01-15
> **abrrymnvette said:**
> Are your interfaces up? If you type ifconfig in a command prompt what comes back? 

For some reason mine wouldn't come back up after updates. Reboot fixed it.

this is output
```

user@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:9b:6f:93  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1b:57:1d:eb:4d  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:57ff:fe1d:eb4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6219 (6.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:926 (926.0 B)  TX bytes:926 (926.0 B)

```

---

### Post by Ilalmi on 2010-01-16
You have two cards with the same ip-address. Are both cards shown in the network manager?

You don't have to use pppoeconf any more. There is an option now in the network manager: [http://help.ubuntu.com/9.10/internet/C/connecting-dsl.html](http://help.ubuntu.com/9.10/internet/C/connecting-dsl.html)

---

### Post by new_to_ubun2 on 2010-01-16
> **Ilalmi said:**
> You have two cards with the same ip-address. Are both cards shown in the network manager?

You don't have to use pppoeconf any more. There is an option now in the network manager: [http://help.ubuntu.com/9.10/internet/C/connecting-dsl.html](http://help.ubuntu.com/9.10/internet/C/connecting-dsl.html)
Yes both are shown like this-
ifupdown(eth0)
ifupdown(eth1)

I am alredy done with adding up new dsl connection there also I've filled IPv4 setting manually only problem is I don't know what to fill up in service,mac address,search domains

---

### Post by Ilalmi on 2010-01-16
You shouldn't have the same ip address on both network cards. Try changing one of the addresses to 192.168.1.2.

As I understand it, you don't have a router in your network and your pc is connected directly to your dsl modem and has to use this modem to dial into the internet. 
When adding a new dsl connection:

[LIST]
[*]you can leave the fields "service" and "search domain" blank (if your internet service provider didn't tell you otherwise). The "mac address" is a unique address of your network card. At what point does the network manager ask for that?
[*]are you sure, you have to set the ip address manually? You very probably have to set the ip4 configuration to "automatic" to automatically get an ip address assigned by your internet service provider.
[/LIST]

---

### Post by new_to_ubun2 on 2010-01-17
> **Ilalmi said:**
> You shouldn't have the same ip address on both network cards. Try changing one of the addresses to 192.168.1.2.

As I understand it, you don't have a router in your network and your pc is connected directly to your dsl modem and has to use this modem to dial into the internet. 
When adding a new dsl connection:

[LIST]
[*]you can leave the fields "service" and "search domain" blank (if your internet service provider didn't tell you otherwise). The "mac address" is a unique address of your network card. At what point does the network manager ask for that?
[*]are you sure, you have to set the ip address manually? You very probably have to set the ip4 configuration to "automatic" to automatically get an ip address assigned by your internet service provider.
[/LIST]

Yes, I don't have any router
As you suggested added new dsl connection leaving mac address blank
but it didn't worked
Do I need to add dsl connection along with the wired connection? what is difference between them?
I am having this problem on my laptop,what I did on my pc having Ubuntu 8.04 is simply sudo pppoeconf and it works very fine, But it don't works with ubuntu 9.10 is this bug [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/453640]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/453640") causing problem or what?
without internet connection how to fix it :-k

---

### Post by new_to_ubun2 on 2010-01-17
I really appreciate your help Ilalmi
But problem is now solved :)
I reinstalled ubuntu 9.10 and without setting up any connection added dsl connection with sudo pppoeconf and it worked...!! :)
Again thank you for your support.

---

### Post by Ilalmi on 2010-01-17
I'm glad you could solve your problem. Have fun :-)

---

