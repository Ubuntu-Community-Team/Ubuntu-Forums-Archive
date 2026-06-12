---
title: "Onboard Lan - No -- PCI Card Yes ??"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by geoff511 on 2008-06-03
Just swapped m/board from an Intel to an AMD.
Must say Ubuntu 8.04 is fantastic! Just started and kept going, had to remind myself I changed the m/board, no "blue-screen" of death, drivers to look for, re-boot after re-boot -- it just accepted it !!   really nice & easy.

Problem is the network.
Used to use a PCI card on old m/board.
New m/board has onboard lan. 
It seems to work, lights flicker on router, no little error stars near network icon on system tray, but when I try to access Internet or Networked drives - nothing, just sits there and then after a minute or so, says can't find it.
Checked the wired setting and says IP address , DNS etc all zeros ??

Plugged in a PCI card (different one to used before as it went with m/baord) and all up and running fine.

Anybody got an idea on why onboard lan didn't work ?? and what to look for to try and get it to find the IP address etc. ??

Or are some onboard lans just not supported ?? no matter if this is the case, just curious as am trying to learn and understand Ubuntu.

Thanks

---

### Post by iaculallad on 2008-06-03
You might try to verify your Onboard LAN with sudo lshw.

```
sudo lshw
```

Post it if you can.

---

### Post by geoff511 on 2008-06-03
sorry delay getting back to you ...

here is what came up re-network -

 *-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth1
                version: 19
                serial: 00:13:d4:fa:28:ca
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
        *-pci:5
             description: PCI bridge
             product: K8T890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: c
             bus info: pci@0000:00:0c.0
             logical name: eth0
             version: 10
             serial: 00:40:95:30:17:e7
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.104 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s


(The realtek is the PCI card)

---

### Post by iaculallad on 2008-06-03
Post the result of your ifconfig

---

### Post by geoff511 on 2008-06-03
Plugged cable into lan port - this time showed a small red cross near tray icon and this was the printout from sudo lshw

*-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth1
                version: 19
                serial: 00:13:d4:fa:28:ca
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
        *-pci:5
             description: PCI bridge
             product: K8T890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: c
             bus info: pci@0000:00:0c.0
             logical name: eth0
             version: 10
             serial: 00:40:95:30:17:e7
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

---

### Post by geoff511 on 2008-06-03
sorry,
where or how do i find ifconfig ??

---

### Post by geoff511 on 2008-06-03
found it - 


eth0      Link encap:Ethernet  HWaddr 00:40:95:30:17:e7  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:95ff:fe30:17e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1675862 (1.5 MB)  TX bytes:383467 (374.4 KB)
          Interrupt:21 Base address:0xb000 

eth1      Link encap:Ethernet  HWaddr 00:13:d4:fa:28:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:24 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47000 (45.8 KB)  TX bytes:47000 (45.8 KB)

---

### Post by iaculallad on 2008-06-03
Not enough info, try posting your /etc/network/interfaces

In the terminal:

```
cat /etc/network/interfaces
```

---

### Post by geoff511 on 2008-06-03
this is what came up ... 

cat /etc/network/interfaces
auto lo
iface lo inet loopback

as said few messages back, if I plug the cable into the onbaord lan and it shows a red cross near network icon.

Could that mean it's just not supported, or are there drivers i could use ?

---

### Post by iaculallad on 2008-06-03
On your terminal:

-Bring down the connection on eth0 (External LAN card?) and bring up eth1(Internal LAN card?):

```
sudo ifconfig eth0 down
sudo ifconfig eth1 up
```

-Edit /etc/network/interfaces

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
sudo gedit /etc/network/interfaces
```

-Delete all lines of text on your current /etc/network/interfaces file and replace it with the codes below.

```
auto lo
iface lo inet loopback
iface eth1 inet static
address 192.168.0.104
netmask 255.255.255.0
gateway 192.168.0.**x**
auto eth1
```

-Open up another terminal and issue the command **netstat -rn** to get your default gateway which you need to replace the **x** (for gateway 192.168.0.**x**) on what you pasted above.

```
netstat -rn
```

-Save the file, Connect UTP cable on the internal LAN card and on the terminal, issue the command below to restart your network.

```
sudo /etc/init.d/networking restart
```

NOTE: disregard the netstat -rn command and remove the gateway in your /etc/network/interfaces. We already killed the connection so you cannot get your default gateway.

---

### Post by geoff511 on 2008-06-03
no that didn't work ...
this is what is diplayed - 

*reconfiguring network interfaces ...
SIOCADDRT: no such process
Failed to bring up eth1

When plugged into onbaord lan - no red cross on tray icon, can find itself on network, but times out finding network drives, and can't find internet.

Plug back into PCI card, can't find itself, network or internet.

---

### Post by geoff511 on 2008-06-03
changed gateway address from 0 to 1 ...
this time no error message when run netsat -rn
find itself, no network drives, no internet

restarted computer,
no red cross on network icons, took ages for light to appear on router, when tried to access internet - light on router went out.

minute later light came back on - no network found, no internet
then found itself and light went back out

---

### Post by geoff511 on 2008-06-03
Thanks iaculallad - i know i am a bit of a pain not knowing this stuff.

still not working properly but am looking in the right direction now, thanks.
Will try a couple of different things and see what happens, am wondering if could be router ?? i am using a d-link di-624+ , but it says it can see the linux machine on 192.168.0.104  so ??

all the best and once again thankyou.

---

