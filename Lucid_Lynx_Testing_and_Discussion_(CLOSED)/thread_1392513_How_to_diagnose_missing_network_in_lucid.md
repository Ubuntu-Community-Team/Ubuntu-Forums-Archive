---
title: "How to diagnose missing network in lucid?"
date: 2010-01-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Dave-B on 2010-01-28
Hi,

I've just made a new install of a daily Lucid image and it looks great - except that it won't join the wired network.

Running `ifconfig eth0` gives no "inet" line* - does that mean that it isn't configured for IP4, or that there's no IP4 connection present?

Editing "Auto eth0", the IPv4  Settings are set to Automatic (DHCP)

Any pointers appreciated!

Cheers,
Dave.


* There is inet6, but I don't think we run that.

---

### Post by cariboo on 2010-01-28
Make sure the driver for you nic is loaded by running:

```
sudo lshw -C network
```

On my system my nic is a bridge device, the output looks something like this:

```
*-bridge
       description: Ethernet interface
       product: MCP61 Ethernet
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: a2
       serial: 00:24:21:da:4e:f4
       size: 100000000
       capacity: 100000000
       width: 32 bits
       clock: 66MHz
       capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=forcedeth** driverversion=0.64 duplex=full ip=192.168.1.215 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:27 memory:ddf7d000-ddf7dfff ioport:ee00(size=8)
```

I have highlighted the driver section, you should see something similar if your device is detected and the driver is loaded.

---

### Post by doas777 on 2010-01-28
> **Dave-B said:**
> Hi,

I've just made a new install of a daily Lucid image and it looks great - except that it won't join the wired network.

Running `ifconfig eth0` gives no "inet" line* - does that mean that it isn't configured for IP4, or that there's no IP4 connection present?

Editing "Auto eth0", the IPv4  Settings are set to Automatic (DHCP)

Any pointers appreciated!

Cheers,
Dave.

* There is inet6, but I don't think we run that.

the "No Inet line" error may be a reference to your /etc/network/interfaces file.
here is some info on how to set up the file:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

just make sure that there is a line like:
```

auto eth0
iface eth0 inet {dhcp|static}

```

hopefully that will do ya

---

### Post by cariboo on 2010-01-28
Unfortunately trying to setup networking manually through /etc/network/interfaces doesn't work any more, it has to be setup using Network-Manager. Static ip addresses can be set in /etc/NetworkManager/system-connections/Auto ethX. In my case it's eth0, but other systems may be different.

---

### Post by doas777 on 2010-01-28
> **cariboo907 said:**
> Unfortunately trying to setup networking manually through /etc/network/interfaces doesn't work any more, it has to be setup using Network-Manager. Static ip addresses can be set in /etc/NetworkManager/system-connections/Auto ethX. In my case it's eth0, but other systems may be different.
thank you for that update. I would not have suspected that that was one of the things that changed in lucid.

---

### Post by zika on 2010-01-28
> **cariboo907 said:**
> Unfortunately trying to setup networking manually through /etc/network/interfaces doesn't work any more, it has to be setup using Network-Manager. Static ip addresses can be set in /etc/NetworkManager/system-connections/Auto ethX. In my case it's eth0, but other systems may be different.I'm using it all the time... Right now. On Lucid. With or without NM installed. Just listing ethX in /etc/network/interfaces takes it from NM and You can control it... Edit /etc/NetworkManager/nm-system-settings.conf accordingly, to let ifupdown manage ethX... switch is managed={true,false}.

---

### Post by Dave-B on 2010-01-29
> **cariboo907 said:**
> Make sure the driver for you nic is loaded by running:

```
sudo lshw -C network
```


Yup, I get similar, but with driver=e1000 driverversion=7.3.21-k5-NAPI

Cheers,
D.

---

### Post by Dave-B on 2010-01-29
> **doas777 said:**
> the "No Inet line" error may be a reference to your /etc/network/interfaces file.


Clarification: I don't actually get an error saying "No Inet line". 

For ifconfig, instead of something like:
```

eth0      Link encap:Ethernet  HWaddr 00:17:9A:0A:F6:44
          inet addr:192.168.2.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fe0a:f644/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:227614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60421 errors:0 dropped:0 overruns:0 carrier:0
          collisions:272 txqueuelen:1000
          RX bytes:69661583 (66.4 MiB)  TX bytes:10361043 (9.8 MiB)
          Interrupt:17

```

...I get something like:
```

eth0      Link encap:Ethernet  HWaddr 00:17:9A:0A:F6:44
          inet6 addr: fe80::217:9aff:fe0a:f644/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:227614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60421 errors:0 dropped:0 overruns:0 carrier:0
          collisions:272 txqueuelen:1000
          RX bytes:69661583 (66.4 MiB)  TX bytes:10361043 (9.8 MiB)
          Interrupt:17

```

(I've no copy & paste from that machine, so the exact details aren't relevant.)
Note the line beginning "inet addr:" is missing.


> 
here is some info on how to set up the file:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

just make sure that there is a line like:
```

auto eth0
iface eth0 inet {dhcp|static}

```

hopefully that will do ya

I've tried it with and without that section, and auth eth0 appears in Network Manager in both cases - but with out the "inet addr:" :-(

So would that mean that it isn't configured for IP4, or that there's no IP4 connection present?

Cheers,
Dave.

---

### Post by cariboo on 2010-01-29
Have you tried opening a terminal and running:

```
sudo dhclient eth0
```

---

### Post by doas777 on 2010-01-29
> **Dave-B said:**
> 

So would that mean that it isn't configured for IP4, or that there's no IP4 connection present?
it most likely means that you just don't have an address assigned either via dhcp or a static configuration.

---

### Post by Dave-B on 2010-02-02
Hi all, thanks for your help.

Yes, it turns out that the system is definitely configured for IP (and it's working).
The line beginning "inet addr:" only appears if the machine has successfuly aquired an address.

Cheers,
Dave.

---

### Post by itsjustarumour on 2010-03-09
> **cariboo907 said:**
> Have you tried opening a terminal and running:

```
sudo dhclient eth0
```

I was getting exactly the same thing as Dave-B, and this command fixed it for me.  Strangely all the Network-Manager settings were correct, and once my machine picked up an IP address the Network-Manager applet still showed as connecting, and over an hour later is still trying...

---

