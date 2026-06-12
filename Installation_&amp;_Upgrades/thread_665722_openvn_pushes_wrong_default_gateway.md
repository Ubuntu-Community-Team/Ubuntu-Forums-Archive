---
title: "openvn: pushes wrong default gateway"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by saqibm on 2008-01-12
i have installed openvpn server, it seems to work but when i add 
push "redirect-gateway def1"
to the server.conf it pushes the wrong default gateway to the client.
my understanding  is that the above line should push the server's vpn ip as the default gateway for all traffic. that connects to the server so where does it get the idea that the vpn ip pool starts at x.x.x.5
and that the dhcp/dns/gateway is x.x.x.5? 

any help would be appreciated.

here is ifconfig tun0 on server
```

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  

          inet addr:10.1.2.1  P-t-P:10.1.2.2  Mask:255.255.255.255

          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:100 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```


and when the client is connected on a windows machine here is the 
ipconfig

```


Ethernet adapter Local Area Connection 3:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : TAP-Win32 Adapter V8
        Physical Address. . . . . . . . . : 00-FF-0C-61-DD-44
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.1.2.6
        Subnet Mask . . . . . . . . . . . : 255.255.255.252
        Default Gateway . . . . . . . . . : 10.1.2.5
        DHCP Server . . . . . . . . . . . : 10.1.2.5
        Lease Obtained. . . . . . . . . . : Saturday, January 12, 2008 3:33:44 PM
        Lease Expires . . . . . . . . . . : Sunday, January 11, 2009 3:33:44 PM

```

and here is the server.conf

```


port 1194

proto udp

dev tun

ca keys/ca.crt

cert keys/server.crt

key keys/server.key  # This file should be kept secret

dh /etc/openvpn/keys/dh1024.pem

server 10.1.2.0 255.255.255.0

ifconfig-pool-persist ipp.txt



push "route 10.1.1.0 255.255.255.0"

keepalive 10 120

comp-lzo

user nobody

group nogroup

persist-key

persist-tun

status openvpn-status.log

verb 6

push "redirect-gateway def1"


```


and here is the client.opvn from the windows machine

```


client


dev tun


proto udp

remote xxx.xxx.xxx 1194

resolv-retry infinite

nobind

# Try to preserve some state across restarts.
persist-key
persist-tun


ca ca.crt
cert home.crt
key home.key

comp-lzo

verb 6

```

---

### Post by hoooool on 2008-07-16
i have exaclty the same problem,... :(

edit: problem solved now ;-) , take a look at [http://ubuntuforums.org/showthread.php?t=727471](http://ubuntuforums.org/showthread.php?t=727471) to solve the problem

---

### Post by Pitt Stains on 2008-07-20
In my setup, my OpenVPN server sits behind a router rather than being exposed right out on the internet.  The /etc/init.d/bridge script that this guy is using ([http://www.thebakershome.net/openvpn_tutorial](http://www.thebakershome.net/openvpn_tutorial)) worked for me.  There's a lot of good stuff in this tutorial as well as the comments below it.

---

