---
title: "Installed and completed Ubuntu Server LTS Ver 14.04 network failed after reboot."
date: 2014-06-07
forum: Installation &amp; Upgrades
---

### Post by kgordon-0 on 2014-06-07
I believe I successfully installed Ubuntu Server LTS Ver 14.04. During the install I formatted the disk which ended 2.5 years of using 11.10 as a website. I also manually configured the network on eth1: ip address 192.168.2.3 mask 255.255.255.0 gateway 192.168.2.1 name server 203.96.152.4 203.96.152.12 8.8.8.8 which I believe worked 100% during the install.
I did not receive any messages during the install. Immediately after the first reboot I ran #w3m [www.google.co.nz]("http://www.google.co.nz") which failed. #w3m localhost was successful. In /etc/bind/named.conf.options I included forwarders same as above. Ran #service bind9 restart. #w3m [www.google.co.nz]("http://www.google.co.nz") long wait with "opening socket... then w3m: Can't load [www.google.co.nz]("http://www.google.co.nz") Looked at many internet topics like: "Problem with setting static ip on Ubuntu Server 14.04" Network unreachable. Learnt not to use #service networking restart as in install instructions but use #ifdown --exclude=lo -a && ifup --exclude=lo -a
Tried many commands like: #dig Ubuntu.com and #nslookup [www.google.com]("http://www.google.com") 8.8.8.8 also failed. Can't #ping 192.168.2.1 (my gateway). Used #route -n and #ethtool eth1 and but to me these look ok.
I wish I could install usbmount then I could transfer the output to my email pc! No network to use apt-get! It was working ok on ver 11.10 six hours ago. So nothing wrong with Smoothwall.
With network I am not much better than a beginner but willing to follow a sequence of steps. Your help would be much appreciated. Kevin

---

### Post by rahul4557 on 2014-06-07
goto
> cd/etc/network/

sudo vi interfaces

It should be in this format

> auto eth0
iface eth0 inet static
address 192.168.2.3
netmask 255.255.255.0
gateway 192.168.2.1
dns-nameservers 8.8.8.8 
dns-search local

then 
restart networking service.

---

### Post by kgordon-0 on 2014-06-07
Thank you for your reply Rahul4557. I made a copy of the interfaces file then created a new file:
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet static
address 192.168.2.3
netmask 255.255.255.0
gateway 192.168.2.1
dns-nameservers 203.96.152.4
dns-search local

then ran:
#ifdown --exclude=lo -a && ifup --exclude=lo -a
(no output)
#ping 192.168.2.1
(destination host unreachable)
#nslookup google.com 8.8.8.8
(;;connection timed out; no servers could be reached)
#ifconfig eth1
eth1 Lin encap:Ethernet HWaddr 00:02:a5:4e:95:e7
       UP BROADCAST MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0(0.0 B) TX bytes:0(0.0 B)
#route -n
Kernel IP routing table
Destination  Gateway  Genmask        Flags  Metric  Ref  Use  Iface
0.0.0.0       192.168.2.1  0.0.0.0        UG        0       0      0     eth1
192.168.2.0  0.0.0.0   255.255.255.0  U          0       0      0     eth1

#ethtool eth1
Settings for eth1:
Supported ports: [IP]
Supported link nodes: 10baseT/Half 10baseT/Full
                                 100baseT/Half 100baseT/Full
                                 1000baseT/Full
Supported pause frame use: No
Supports auto-negotiation: Yes
Advertised link nodes: 10baseT/Half 10baseT/Full
                                 100baseT/Half 100baseT/Full
                                 1000baseT/Full
Advertised pause frame use: No
Advertised auto-negotiation: Yes
Speed: Unknown!
Duplex: Unknown! (255)
Port: Twisted Pair
PHYAD: 0
Transceiver: internal
Auto-negotiation: on
MDI-X: Unknown(auto)
Supports wake-on: umbg
Wake-on: g
Current message level: 0x00000007 (7)
                                  drv probe link
Link detected: No

#dig -x 127.0.0.1
;<<>> DIG 9.9.5-3-Ubuntu <<>> -x 127.0.0.1
;; global options: +cmd
;; connection timed out; no servers could be reached

Hope this helps.
Kevin

---

### Post by kgordon-0 on 2014-06-07
My server uses Broadcom Corp NetXtreme BCM5715.
Is the driver a tg3?
If it is should the driver be provided by the install CD?
Does #insmod tg3.ko on Ubuntu Server LTS Version 14.04 tell me if it is up and running?
Your help would be much appreciate.
Kevin

---

### Post by steeldriver on 2014-06-07
You should be able to use 

```

sudo lshw -C network -sanitize

```

to see the driver status of the interface device(s). Based on your ifconfig output it certainly looks like your interface is not getting an IPv4 address.

---

### Post by kgordon-0 on 2014-06-08
Thank you for the reply.
sudo lshw -C network -sanitize
There are 4 networks: 3 are disabled. I am only using one (but which one?)
*-network:0 DISABLED
        product: 82546EB (Copper)
*-network:1
       product: 82546EB (Copper)
*-network:0 DISABLED
        product: NetXtreme
*-network:1 DISABLED
       product: NetXtreme
I believed I was using the NetXtreme during the past 2.5 years (Ubuntu 11.10 with tg3) for eth1.
sudo ethtool -I eth1
        driver: e1000
Yet the 11.10 install associated eth1 with Broadcom Corp NetXtreme BCM5715
Same port outlet. Same hardware.
14.04 install associates eth1 with Intel?
sudo lsmod
tg3 166442 0
ptp  18933 1 tg3
e1000 145174 0
Could this mean that the wrong driver is loading for eth1?
Or have I used the wrong eth number?
Thanks.

---

### Post by kgordon-0 on 2014-06-08
To summarise:
In the same hardware I previously ran Ubuntu 11.10 which used eth1 (tg3) of a 4 port system (2 internal 1 lights out).
End of life forced me to do a new install of Ubuntu 14.04 which completed using eth1.
After a reboot no internet so changed to eth3:
#ifconfig eth3 192.168.2.3 up
#ifconfig eth0 192.168.2.2 down
#ifconfig eth1 192.168.2.4 down
#ifconfig eth2 192.168.2.5 down
#route all default gw 192.168.2.1
#nslookup google.com 8.8.8.8 (It works!)
Thank you for your help.
Kevin.

---

