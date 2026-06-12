---
title: "First Problem with Ubuntu 9.10 beta"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by junkieweb on 2009-10-04
Hi,

I am an absolute newbie to linux & ubuntu ...

My problem is after installing ubuntu 9.10 successfully ... NO wired network is working ... I add the settings manually, but nothing works ...

My network settings under windows 7 7600 works great, but not on linux ... Please help me connect to the internet ... :(

[[IMG]http://lookpic.com/i/316/3JurjHM7.png[/IMG]]("http://lookpic.com/i/316/3JurjHM7.png")

[[IMG]http://lookpic.com/i/343/Ouo8nYrE.png[/IMG]]("http://lookpic.com/i/343/Ouo8nYrE.png")

[[IMG]http://lookpic.com/i/517/W8olM2qJ.png[/IMG]]("http://lookpic.com/i/517/W8olM2qJ.png")

---

### Post by nhasian on 2009-10-04
when your booted into ubuntu, can you give us the output of the following terminal commands:

```
lshw -C network
```

```
ifconfig
```

---

### Post by CmdGabriel on 2009-10-04
Is it wise to use a BETA version, if you are an absolute beginner?

---

### Post by Zoot7 on 2009-10-04
> **CmdGabriel said:**
> Is it wise to use a BETA version, if you are an absolute beginner?
No most certainly not, Beta releases are intended for testing only for a reason. You'd be far better off you stuck to Jaunty of the current LTS Hardy.

---

### Post by junkieweb on 2009-10-05
OK,

junkieweb@junkieweb-desktop:~$ lshw -C network


WARNING: you should run this program as super-user.
  *-network               
       

description: Ethernet interface
       
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       
vendor: Realtek Semiconductor Co., Ltd.
       
physical id: 0
       
bus info: pci@0000:03:00.0
       
logical name: eth0
       
version: 02
       
serial: 00:1f:d0:00:a0:79
       
width: 64 bits
       
clock: 33MHz
       
capabilities: bus_master cap_list rom ethernet physical
       
configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI 
latency=0 
multicast=yes
       
resources: irq:27 ioport:d000(size=256) 
memory:e3010000-e3010fff(prefetchable) 
memory:e3000000-e300ffff(prefetchable) 
memory:e3020000-e302ffff(prefetchable)


junkieweb@junkieweb-desktop:~$ 

Link
          
UP BROADCAST RUNNING MULTICAST  
MTU:1500  Metric:1
          
RX packets:8 errors:0 dropped:0 
overruns:0 frame:0
          
TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:480 (480.0 B)  TX bytes:3546 (3.5 KB)
          
Interrupt:27 Base address:0xa000 lo        
Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

junkieweb@junkieweb-desktop:~$ 






junkieweb@junkieweb-desktop:~$ ifconfig


eth0      

Link encap:Ethernet  
HWaddr 00:1f:d0:00:a0:79  
  
inet6 addr: fe80::21f:d0ff:fe00:a079/64 
Scope

---

### Post by random turnip on 2009-10-05
> **Zoot7 said:**
> No most certainly not, Beta releases are intended for testing only for a reason. You'd be far better off you stuck to Jaunty of the current LTS Hardy.

+1
9.10 is not yet completely stable, if i were you i would think about sticking to 9.04 for now, 9.10's release isn't even far away.

---

### Post by slakkie on 2009-10-05
Hi,

please have a look at 

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)

or 

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)

The latter is a rewrite of the first guide + newly added content.

---

### Post by louieb on 2009-10-05
Just a quick note about my experience. Installed v9.10 beta using alternate CD - no internet connection. Pretty much got the same as the Original Poster - never did get a wireless connection. (Did not try real hard either).

Try 2: Installed v9.10 beta - this time plugged into a wired internet connection. Upon reboot - wireless connection worked too. 

Still working through other smaller problems with the 9.10 beta. Such as Update manager only doing a partial upgrade, setting preferences for some applets I want to use. Seems the preference dialogs have moved or are not in place yet. 

Karmic beta is not ready for an inexperienced Linux user yet. Unless you have lots of time and nothing else to do.

---

### Post by meborc on 2009-10-05
please refer to karmic sub-forum... the no-internet problem has been reported already

---

### Post by junkieweb on 2009-10-05
well, :(:confused::(
I am sorry but I can't seem to make t work or to understand what the listed terms "codes" mean ... I am a zero in the linux users history ... :(

I think I would wait for the final release or would try linuxmint 7 instead ...

THANX,

---

