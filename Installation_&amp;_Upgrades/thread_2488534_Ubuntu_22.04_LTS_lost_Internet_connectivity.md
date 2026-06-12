---
title: "Ubuntu 22.04 LTS lost Internet connectivity"
date: 2023-07-08
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2023-07-08
Late yesterday afternoon Ubuntu 22.04 LTS can't get on the Internet anymore. It was running fine all week until losing Internet yesterday. Right now everything else plays/runs fine on 22.04 LTS. The only thing I can't do is get on the Internet. Called up my Internet provider and they checked all their equipment, Modem, Router, connections, signal strengths, etc, and they said all is fine on their end. Told me something must be amiss with my PC shown in my signature line below. 

My i7 PC also has Windows 10, along with Ubuntu 20.04 LTS, and Ubuntu 18.04 LTS, and Ubuntu 16.04 LTS, besides running Ubuntu 22.04 LTS. They all run fine on 3 SSDs. Out of curiosity I decided to boot up Windows 10 and it ran fine, getting on the Internet with no problems. Same goes for Ubuntu 20.04 LTS which runs fine on the Internet. Am using 20.04 LTS right now to post this problem I am having with 22.04 LTS.

Anyone got any ideas what went wrong with 22.04 LTS, that keeps me off the Internet? Hope there is a simple fix.

---

### Post by MAFoElffen on 2023-07-08
Wireless or wired connection?

What does it show doing 
```

ip a

```

---

### Post by cybrsaylr on 2023-07-08
I use a wired connection for both 22.04 and 20.04

Here's what code: ip a shows on 20.04

> Studio-XPS-8000:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:25:64:dd:0e:a8 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.250/24 brd 192.168.1.255 scope global dynamic noprefixroute enp5s0
       valid_lft 33217sec preferred_lft 33217sec
    inet6 2603:7081:7438:257f::13e2/128 scope global dynamic noprefixroute 
       valid_lft 413000sec preferred_lft 413000sec
    inet6 2603:7081:7438:257f:c49:8056:bbdf:2d0f/64 scope global temporary dynamic 
       valid_lft 422942sec preferred_lft 75963sec
    inet6 2603:7081:7438:257f:41b2:5549:23fd:82d3/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 422942sec preferred_lft 422942sec
    inet6 fe80::ba2:c8b6:2fbe:419b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 0c:ee:e6:bb:92:18 brd ff:ff:ff:ff:ff:ff


Not sure how to show that for 22.04, since I am using 20.04 right now.

---

### Post by cybrsaylr on 2023-07-08
OK I shut down 20.04.
Did a restart of 22.04, open Terminal, put in code: ip a and got the results, then saved it and moved that file from 22.04 to 20.04 and posted the results below.

Here's a results of code: ip a for 22.04 LTS

> Studio-XPS-8000:~/Desktop$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp5s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 00:25:64:dd:0e:a8 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.250/24 brd 192.168.1.255 scope global dynamic noprefixroute enp5s0
       valid_lft 43180sec preferred_lft 43180sec
    inet6 2603:7081:7438:257f::1ca9/128 scope global dynamic noprefixroute 
       valid_lft 422962sec preferred_lft 422962sec
    inet6 2603:7081:7438:257f:da7d:48c:3981:29fe/64 scope global temporary dynamic 
       valid_lft 422963sec preferred_lft 86163sec
    inet6 2603:7081:7438:257f:8974:371b:7415:3d14/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 422963sec preferred_lft 422963sec
    inet6 fe80::68e1:460f:b4e7:6f3d/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 0c:ee:e6:bb:92:18 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.120/24 brd 192.168.1.255 scope global dynamic noprefixroute wlan0
       valid_lft 43185sec preferred_lft 43185sec
    inet6 2603:7081:7438:257f::1fb1/128 scope global dynamic noprefixroute 
       valid_lft 422969sec preferred_lft 422969sec
    inet6 2603:7081:7438:257f:ca4f:bd84:9302:c03a/64 scope global temporary dynamic 
       valid_lft 422970sec preferred_lft 85813sec
    inet6 2603:7081:7438:257f:c4d2:f50f:3415:e1c1/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 422970sec preferred_lft 422970sec
    inet6 fe80::c4b3:8e44:e54f:de52/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: ipv6leakintrf0: <BROADCAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether 26:2c:c2:ae:81:53 brd ff:ff:ff:ff:ff:ff
    inet6 fdeb:446c:912d:8da::/64 scope global noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::18f2:87e7:cef:80e3/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


While back in 22.04 did again try but still could not get on the Internet.

---

### Post by MAFoElffen on 2023-07-08
It's getting an Ip address assigned as "192.168.1.250" and the status is "UP", that's a start.

Now do 
```

ping -c 4 192.168.1.1

```
If that works, then try
```

ping -c 4 8.8.8.8

```
If that works, then try
```

ping -c 4 www.google.com

```
Tell me where that works and when not.

Stop were that breaks... If it doesn't do something, then there is no need to go on. Just skip and post back.

Then do this
```

cat . /etc/netplan/*.yaml

```

---

### Post by cybrsaylr on 2023-07-08
MAFoElffen, 

Here's the results I got:

$ ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.755 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.349 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.351 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.368 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3077ms
rtt min/avg/max/mdev = 0.349/0.455/0.755/0.172 ms
t22@t22-Studio-XPS-8000:~/Desktop$ ping -c 4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=58 time=30.4 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=58 time=23.2 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=58 time=24.8 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=58 time=22.5 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 22.486/25.234/30.434/3.119 ms
t22@t22-Studio-XPS-8000:~/Desktop$ ping -c 4 [www.google.com](www.google.com)
ping: [www.google.com:](www.google.com:) Temporary failure in name resolution
t22@t22-Studio-XPS-8000:~/Desktop$ cat . /etc/netplan/*.yaml
cat: .: Is a directory
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

---

### Post by MAFoElffen on 2023-07-08
Go to "Setting" > "Network" > "Wired"... Describe to me which profiles you see listed there. Is there only one?

If only one (Wired Connection 1), then select the gear icon on the left of the profile name. Select the IPv4 tab. Select the Manual radio button...

In the dialog box at the bottom... 

Under "Address", type: 192.168.1.5
Under "Netmask", type: 255.255.255.0
Under "Gateway", type 192.168.1.1

Select the "Apply" button in the upper right corner.

Close Settings.

Try to pig those addresses again, starting with the first that it failed on, until you get through the list...

---

### Post by MAFoElffen on 2023-07-08
If that works... It should. Then log into a launchpad.net account... You should be able to log in with the UbuntuOne Account that you log into this Forum with. If not create one.

Join this Bug Report as "This affects me"... [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986)

I noticed that a few weeks ago, that an update caused the only laptop I have that wasn't set with a static IP address to not be able to connect as a DHCP client... But if I set a static IP address, that it works fine. So there seems to be a bug with the current DHCP client package somewhere.

---

### Post by cybrsaylr on 2023-07-09
Finally got around to do, or trying to do what you recommended.
 

> **MAFoElffen said:**
> Go to "Setting" > "Network" > "Wired"... Describe to me which profiles you see listed there. Is there only one?

Try to pig those addresses again, starting with the first that it failed on, until you get through the list...

Here's what I get for "Setting" > "Network" > "Wired", where that gear icon is on the right for me?

[IMG]https://i.postimg.cc/8C74Pvjx/Screenshot-2023-07-09.png[/IMG]

Tried doing what you said with IPv4 tab but nothing seemed to work, or I did it wrong.

Not sure what you meant by "Try to pig those addresses again..."

---

### Post by MAFoElffen on 2023-07-10
Select that Gear shaped Icon to the right of that radio On/Off slider button... See attached

---

