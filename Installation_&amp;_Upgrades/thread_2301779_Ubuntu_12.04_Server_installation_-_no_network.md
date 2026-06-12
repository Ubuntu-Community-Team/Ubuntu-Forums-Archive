---
title: "Ubuntu 12.04 Server installation - no network"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by aaron27 on 2015-11-05
I have just installed a new 12.04 machine and I cannot get the commands  > sudo apt-get update or > sudo apt-get install  gnome to work, they are not connecting.

I have set this machine a static IP. I have modified the /etc/network/interfaces file to show as below:

```

auto eth0
iface eth0 inet static
address – static ip
netmask 255.255.0.0
gateway gateway ip
dns-nameservers dns server ip's

```

I can confirm the two DNS entries show in /etc/resolv.conf

Previously this has worked fine but I am not sure what I have done wrong (or missed) in this instance

---

### Post by TheFu on 2015-11-05
Post the complete /etc/network/interfaces file.

Also...   [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

---

### Post by aaron27 on 2015-11-06
```


#This file describes the network interfaces available on your system
#and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
              address 'ip address'
              netmask 255.255.0.0
              gateway 'gateway ip'
              dns-nameservers 'dns ip' 'dns ip 2'


```

On that link. Pinging router, server, known internet ip all come back unreachable. pinging google gives me a message saying unknown host.

resolv.conf shows the two same DNS entries from the interfaces file.

Route shows the below:

```



Destination      Gateway            Genmask       Flags      Metric    Ref       Use        iface
default           'gateway ip'        0.0.0.0          UG         100       0            0         eth0
localnet          *                     255.255.0.0     U           0         0             0        eth0



```

Not sure how much this helps?

---

### Post by TheFu on 2015-11-06
That is not a valid interfaces file. Here's one of mine.
```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
  address 172.22.22.13
  gateway 172.22.22.1
  netmask 255.255.255.0
#  mtu 1500
  dns-nameservers 172.22.22.1
```

Real IPs  are needed. There isn't any replacement template engine for this stuff in that  file.

---

### Post by aaron27 on 2015-11-09
I do have IP's in my actual interface file I just dont wish them to be in the public domain. 
My Interfaces file looks the same as yours.

I have been googling this issue and came across an instruction to run the command 

>  arp -a 

This then shows my two DNS IP addresses as incomplete on Eth0

```

:~$ arp -a
? (172.16.10.1) at <incomplete> on eth0
? (172.16.10.14) at <incomplete> on eth0

```

I know both the DNS IP addresses work as I use them on my personal PC.

---

