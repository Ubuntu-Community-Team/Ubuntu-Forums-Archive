---
title: "Ubuntu Edgy network problem"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by wolphin on 2006-10-27
Hi,

I installed Ubuntu Edgy last night, but am having a bit of trouble with the GUI (it's the 'black screen after bootsplash' problem that so many people seem to have - I might try changing xorg.conf later), so I'm working in the CLI at the moment.

My NIC was automatically detected (eth0), but when I try to get it an IP via DHCP (it's connected by patch cable to the router) it attempts to get a lease five times and then fails. Here's the problem:
```
# dhclient eth0
[blah blah]
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
As you can see, it is not receiving any offers from my DHCP server, which is my router. There is nothing wrong with my router, as I've got other hosts on the network which are working perfectly. Please note that, at this point, there were no stored routes, and I couldn't ping anything.

So, I decided to configure the interface manually. I ran the following commands:
```
# ifconfig eth0 192.168.1.105
# ifconfig eth0 netmask 255.255.255.0
# route add default gw 192.168.1.1
```
The first sets a static IP, the second sets the subnet mask, and the third add a route to my router's IP and sets it as the gateway.

Now I can ping all the hosts on my network, but nothing outside it.

I also had a non-existant /etc/resolv.conf (nameserver list), so I created my own, which now reads:
```
nameserver 192.168.1.1
```
My router is also a DNS server.

However, I still can't ping anything outside the network...:
```
# ping google.com
ping: unknown host google.com
```
I do, however, know that it's not a DNS problem, because 'netstat google.com' outputs the IP address, but when I try to ping that address it gives me the same error.

Any ideas? I am, quite frankly, stumped... I think it's some kind of routing problem? The odd thing is that networking worked fine on the old installation of Ubuntu (Dapper), and it's not a problem with the card, because it obviously works. I did a full re-install with the Edgy CD, by the way.

Thanks in advance.

---

