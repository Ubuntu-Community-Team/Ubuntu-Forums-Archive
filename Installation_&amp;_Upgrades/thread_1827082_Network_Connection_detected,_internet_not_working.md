---
title: "Network Connection detected, internet not working"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by 710m_Rookie on 2011-08-17
Hi Guys, i'm new to the Linux world so take it easy on me.

So i installed a linux flavor (Ubuntu 10.04 LTS, Ubuntu 11.04, and then Linux Mint).. They all gave this same problem about the wired network (see the picture). The connection seems to be fine but i can't connect to internet or even to my router. Which is weird since it knows my router IP 192.168.1.79. Wasted the whole night trying to figure it out but i just can't understand why.


I have a separate partition on this computer to run Win7 also and confirmed that the network connection is working.

[IMG]https://lh3.googleusercontent.com/-EnIquQMb_Vw/TkviNbrGIXI/AAAAAAAAc2s/QpiQPw4oxa8/s800/IMG_20110817_084551.jpg[/IMG]

---

### Post by lmarmisa on 2011-08-17
Have you defined the network config manually?. Do you know if your router supports automatic config with DHCP?.

**I did not pay attention that the information of ifconfig is in your previous post.**

---

### Post by lmarmisa on 2011-08-17
Could you post the outputs of these commands?:

```

ping -b -c3 192.168.1.255
ping -c3 192.168.1.79

```

---

### Post by 710m_Rookie on 2011-08-17
> **lmarmisa said:**
> Could you post the outputs of these commands?:

```

ping -b -c3 192.168.1.255
ping -c3 192.168.1.79

```

Will do to night when i get home and report back here.  Thanks for your help.

---

### Post by 710m_Rookie on 2011-08-17
> **lmarmisa said:**
> Could you post the outputs of these commands?:

```

ping -b -c3 192.168.1.255
ping -c3 192.168.1.79

```

No luck there

[IMG]https://lh4.googleusercontent.com/-bm3Y8jQDmUQ/TkxkJqjduoI/AAAAAAAAc28/H2XW4zc4Xv8/s800/IMG_20110817_180009.jpg[/IMG]

---

### Post by 710m_Rookie on 2011-08-17
pinging from my other computer:

C:\Users\Administrator>ping 192.168.1.102

Pinging 192.168.1.102 with 32 bytes of data:
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.

Ping statistics for 192.168.1.102:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

---

### Post by infamous-online on 2011-08-17
> **710m_Rookie said:**
> pinging from my other computer:

C:\Users\Administrator>ping 192.168.1.102

Pinging 192.168.1.102 with 32 bytes of data:
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.

Ping statistics for 192.168.1.102:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

What kind of network card do you have do you know?

---

### Post by 710m_Rookie on 2011-08-17
> **infamous-online said:**
> What kind of network card do you have do you know?

MARVELL PCI Gbit LAN controller : 
- AI NET2

came in A8N-SLI DELUXE MOBO

---

### Post by lmarmisa on 2011-08-17
Please, post the outputs of these commands:

```

nm-tool
sudo lshw -C network
route -n
ifconfig

```

---

### Post by 710m_Rookie on 2011-08-17
```

sun@sun-desktop ~ $ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            skge
  State:             connected
  Default:           yes
  HW Address:        00:15:F2:4A:98:DF

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.79

    DNS:             68.105.28.12
    DNS:             68.105.29.12
    DNS:             68.105.28.11


sun@sun-desktop ~ $ sudo lshw -C network
[sudo] password for sun: 
  *-network               
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:05:0c.0
       logical name: eth0
       version: 13
       serial: 00:15:f2:4a:98:df
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.102 latency=32 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:d300c000-d300ffff ioport:a400(size=256) memory:d4100000-d411ffff
sun@sun-desktop ~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.79    0.0.0.0         UG    0      0        0 eth0
sun@sun-desktop ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:4a:98:df  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe4a:98df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2363 (2.3 KB)  TX bytes:16058 (16.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5130 (5.1 KB)  TX bytes:5130 (5.1 KB)



```

---

### Post by lmarmisa on 2011-08-17
> **710m_Rookie said:**
> pinging from my other computer:

C:\Users\Administrator>ping 192.168.1.102

Pinging 192.168.1.102 with 32 bytes of data:
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.

Ping statistics for 192.168.1.102:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

Hmmm. This output is interesting. You get the message **Destination host unreachable** from the IP address 192.168.1.105. Do you know what is the device answering from that IP address 192.168.1.105?.

Please post the output of this Windows command:

```

ipconfig /all

```I asked in a previous post if your have defined your network configuration manually.

---

### Post by 710m_Rookie on 2011-08-17
no.. i just let DHCP do its things.


Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : ph.cox.net
   Description . . . . . . . . . . . : Broadcom 802.11g Network Adapter
   Physical Address. . . . . . . . . : 00-1E-E5-29-B8-63
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5ca3:9162:1b3a:bc79%12(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.105(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Wednesday, August 17, 2011 7:48:58 PM
   Lease Expires . . . . . . . . . . : Thursday, August 18, 2011 7:52:16 PM
   Default Gateway . . . . . . . . . : 192.168.1.79
   DHCP Server . . . . . . . . . . . : 192.168.1.79
   DHCPv6 IAID . . . . . . . . . . . : 218111717
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-12-DE-D6-D5-6C-F0-49-50-9B-18
   DNS Servers . . . . . . . . . . . : 68.105.28.12
                                       68.105.29.12
                                       68.105.28.11
   NetBIOS over Tcpip. . . . . . . . : Enabled

---

### Post by lmarmisa on 2011-08-17
This output is odd. 

```

C:\Users\Administrator>ping 192.168.1.102

Pinging 192.168.1.102 with 32 bytes of data:
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.
Reply from 192.168.1.105: Destination host unreachable.

Ping statistics for 192.168.1.102:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

```

Your windows computer says that the destination is unreachable but all packets were answered from 192.168.1.102 (0% loss).

Your computer running Windows is able to ping your Mint computer with this odd message.

Have you checked if the computer running Mint (192.168.1.102) is able to ping your other computer (192.168.1.105)?:

```

ping -c4 192.168.1.105

```

I suppose that your router is the same for wired and wireless connections.

---

### Post by 710m_Rookie on 2011-08-18
```

$ ping -c4 192.168.1.105
PING 192.168.1.105 (192.168.1.105) 56 (84) bytes of data.
From 192.168.1.102 icmp seq=1 Destination Host Unreachable
2
3
4 lines

--- 192.168.1.105 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3007ms pipe 3
$

```

---

### Post by 710m_Rookie on 2011-08-18
I think i'm ready to throw in the towel.  At this time and age, an OS that can't get a NIC going can't be good.  I tried a while back version 8.x and i gave it another try now, must not be for me.

Thanks for your help, guys!  Much appreciated.

---

### Post by lmarmisa on 2011-08-18
Hmmm. Maybe Mint and Ubuntu are not guilty. The behavior of your router is suspicious too. 

Mint was able to negotiate the DHCP protocol. Try this command in order to check if you see something strange about DHCP:

```

sudo dhclient3

```Maybe the problem is located in the router. Imagine that the router is expecting the same host name of your computer than when running Windows 7. 

Try to connect to the router from the other computer using the web interface and look for a connected device list or something like that. Do you see the Mint host connected there?.

---

### Post by 710m_Rookie on 2011-08-18
Not sure how can it be the router, i check the DHCP table and each device has its own ip.  Beside when i run windows (dual boot), internet is fast without any hiccup.

Also, I just install freenas on the same machine, set the NIC to DHCP and bam! done;i now have machine that host a web server (ZFS web manager) ...total installation time under 10min.

Tell me that's not an OS issue.

Still, thanks for helping.

---

