---
title: "Please help w/ this network problem"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dxxvi on 2009-10-01
I'm running Karmic (updated & upgraded every day) on a ThinkPad SL500. I run Windows XP Pro SP3 with bridged network adapter in VirtualBox. In XP I install a AT&T VPN client (laptopconnect edition).

The eth0 on Karmic: 192.168.0.100/255.255.255.0. The router to go to the Internet has the ip addr of 192.168.0.1 as can be seen with route -n```
ly@ly-karmic:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```After I run the vpn client on XP, this is what can be seen with ipconfig /all```
Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : AMD PCNET Family PCI Ethernet Adapter
        Physical Address. . . . . . . . . : 08-00-27-96-B5-67
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.101
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 167.206.245.130
                                            167.206.245.129
        Lease Obtained. . . . . . . . . . : Wednesday, September 30, 2009 10:16:21 PM
        Lease Expires . . . . . . . . . . : Wednesday, October 07, 2009 10:16:21 PM

Ethernet adapter AGN Virtual Network Adapter:

        Connection-specific DNS Suffix  . : att.com
        Description . . . . . . . . . . . : AGN Virtual Network Adapter
        Physical Address. . . . . . . . . : 02-50-F2-00-00-05
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 135.70.225.252
        Subnet Mask . . . . . . . . . . . : 255.255.248.0
        Default Gateway . . . . . . . . . : 135.70.225.252
        DNS Servers . . . . . . . . . . . : 135.37.9.18
                                            135.38.244.3
        Primary WINS Server . . . . . . . : 135.37.143.11
        Secondary WINS Server . . . . . . : 135.71.15.34
```I can use putty on the XP virtual machine to access to a pc at 135.217.191.216.

Now I want to use ssh (and other applications) on Karmic to access that machine (135.217.191.216). So this is what I did:

- configure XP as a router: change IPEnableRouter in HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters from 0 to 1.

- add an entry to the Karmic routing table with```
sudo route add -net 135.217.0.0 netmask 255.255.0.0 gw 192.168.0.101
```The routing table is now like this```
ly@ly-karmic:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
135.217.0.0     192.168.0.101   255.255.0.0     UG    0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```

However I still cannot access the machine 135.217.191.216. Could anybody please help me here?

Thank you.

---

### Post by dxxvi on 2009-10-04
I'm still stuck at this problem.

---

### Post by skatinjj on 2009-10-04
Is 135.217.191.216 another virtual machine or a physical box?

Also, is this PC on your network or an outside network?

---

