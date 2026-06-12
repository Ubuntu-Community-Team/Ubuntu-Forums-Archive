---
title: "Ubuntu version which work with the dongle"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by Gins on 2013-02-03
I have a USB dongle. It is from a ISP. The ISP is 'Tre'. I think they are a popular company in Europe.

It works with my Windows 7 laptop computer. 
It does not work with my Ubuntu desktop computer.

Is there an Ubuntu version which works with the dongle?
I always work with Ubuntu.It is Kubuntu
**Your help is deeply appreciated.**

.............................................
ka@ka-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
ka@ka-desktop:~$ 
...........................................

---

### Post by bogan on 2013-02-03
Hi!, **Gins,**

It is not a case of which version of Ubuntu will work with a Wifi USB dongle, but which USB dongle will work with Ubuntu.

Most USB Adapters **will** work with most recent versions of Ubuntu, always provided the correct driver is installed, though some have difficulty achieving 802.11n speeds.

To find the right driver it is necessary to know exactly which chipset is used, so please Post:
What Windows calls it on the Laptop, in Device Manager>Network Adapter.

And, run from a Terminal on the Desktop:
```
lsusb
sudo lshw -C network
rfkill list all
iwconfig
ifconfig
```Chao!, **bogan**.

---

### Post by Gins on 2013-02-03
Thanks bogan

ka@ka-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2101:020f ActionStar 
Bus 002 Device 003: ID 03f0:6104 Hewlett-Packard DeskJet 5650c
ka@ka-desktop:~$ 
&#8230;.................................................

ka@ka-desktop:~$ sudo lshw -C network
[sudo] password for ka: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:13:8f:e2:66:9d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=212.181.210.34 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:36 ioport:e800(size=256) memory:fbfff000-fbffffff memory:fbfc0000-fbfdffff
ka@ka-desktop:~$ 

...............................................................................
ka@ka-desktop:~$ rfkill list all
ka@ka-desktop:~$ 
..............................................................................

ka@ka-desktop:~$ iwconfig                                                                                                                                  
lo        no wireless extensions.                                                                                                                                      
                                                                                                                                                                       
eth0      no wireless extensions.                                                                                                                                      
                                                                                                                                                 ...............................................................................

                   
ka@ka-desktop:~$ ifconfig 

                                                                                                                                 
eth0      Link encap:Ethernet  HWaddr 00:13:8f:e2:66:9d  
          inet addr:212.181.210.34  Bcast:212.181.210.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fee2:669d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58018 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60927691 (60.9 MB)  TX bytes:11163649 (11.1 MB)
          Interrupt:36 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

ka@ka-desktop:~$

---

### Post by Gins on 2013-02-05
I would like to hear from our friends.
My dongle works with Windows 7 laptop, which I use rarely.

I want it to work with my Ubuntu.
Your help is deeply appreciated.

---

### Post by Mark Phelps on 2013-02-05
Give Bogan a chance to get back to you -- reusing Windows based hardware in Linux is NOT a trivial exercise.

---

### Post by Gins on 2013-02-05
Thanks Mark
I know this is not a simple task.
I tried in vain some months ago.

---

