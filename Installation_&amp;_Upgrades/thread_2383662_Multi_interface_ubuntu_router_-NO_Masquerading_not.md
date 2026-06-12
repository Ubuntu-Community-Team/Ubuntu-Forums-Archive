---
title: "Multi interface ubuntu router -NO Masquerading not working"
date: 2018-01-28
forum: Installation &amp; Upgrades
---

### Post by Andrew_Welham on 2018-01-28
Dear All,


I'me trying to build a new router, will be on Ubuntu 18.04 (when its released)
currently i have DDWRT on my router the details can be seen below. The 192.168.0.0/24 subnet works find with an a ubuntu 16.04 router
the new router covers the ranges
192.168.1.0
192.168.2.0
192.168.3.0
192.168.4.0
192.168.5.0
192.168.6.0
192.168.7.0


and has links to the my old network 192.168.0.0 and the internet router network 192.168.0.253.0




The internet router running dd-wrt routing tables look like


ddwrt
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         INTERNETIP      0.0.0.0         UG        0 0          0 ppp0
INTERNETIP      0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
ProvideIP       0.0.0.0         255.255.255.248 U         0 0          0 ppp0
127.0.0.0       0.0.0.0         255.0.0.0       U         0 0          0 lo
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 br0
192.168.0.0     192.168.253.253 255.255.255.0   UG        0 0          0 br0
192.168.1.0     192.168.253.2   255.255.255.0   UG        0 0          0 br0
192.168.2.0     192.168.253.2   255.255.255.0   UG        0 0          0 br0
192.168.3.0     192.168.253.2   255.255.255.0   UG        0 0          0 br0
192.168.4.0     192.168.253.2   255.255.255.0   UG        0 0          0 br0
192.168.5.0     192.168.253.2   255.255.255.0   UG        0 0          0 br0
192.168.6.0     192.168.253.2   255.255.255.0   UG        0 0          0 br0
192.168.7.0     192.168.253.2   255.255.255.0   UG        0 0          0 br0
192.168.253.0   0.0.0.0         255.255.255.0   U         0 0          0 br0




my new router tables look like (this is the one which does not work)
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.253.1   0.0.0.0         UG        0 0          0 enp0s19
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 enp0s3
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 enp0s8
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 enp0s9
192.168.3.0     0.0.0.0         255.255.255.0   U         0 0          0 enp0s10
192.168.4.0     0.0.0.0         255.255.255.0   U         0 0          0 enp0s16
192.168.5.0     0.0.0.0         255.255.255.0   U         0 0          0 enp0s17
192.168.6.0     0.0.0.0         255.255.255.0   U         0 0          0 enp0s18
192.168.7.0     0.0.0.0         255.255.255.0   U         0 0          0 enp0s18
192.168.253.0   0.0.0.0         255.255.255.0   U         0 0          0 enp0s19




The ipaddress allocation on the new router is as shown below. I also have keepalive running on most interfaces


ifconfig -a
enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.3  netmask 255.255.255.0  broadcast 192.168.0.255
enp0s8: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.3  netmask 255.255.255.0  broadcast 192.168.1.255
Keep ALive VIP of 192.168.1
enp0s9: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.2  netmask 255.255.255.0  broadcast 192.168.2.255
Keep ALive VIP of 192.168.2.1
enp0s10: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.3.2  netmask 255.255.255.0  broadcast 192.168.3.255
Keep ALive VIP of 192.168.3.1
enp0s16: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.4.2  netmask 255.255.255.0  broadcast 192.168.4.255
Keep ALive VIP of 192.168.4.1
enp0s17: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.5.2  netmask 255.255.255.0  broadcast 192.168.5.255
Keep ALive VIP of 192.168.5.1
enp0s18: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.6.2  netmask 255.255.255.0  broadcast 192.168.6.255
Keep ALive VIP of 192.168.6.1
enp0s19: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.253.3  netmask 255.255.255.0  broadcast 192.168.253.255
Keep ALive VIP of 192.168.253.2


# tcpdump -n -i enp0s19 | grep -v ARP
when pinging the lan side connection of the internet router (ddwrt)
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on enp0s19, link-type EN10MB (Ethernet), capture size 262144 bytes
11:37:59.049458 IP 192.168.4.20 > 192.168.253.1: ICMP echo request, id 3928, seq 210, length 64
11:37:59.050082 IP 192.168.253.1 > 192.168.4.20: ICMP echo reply, id 3928, seq 210, length 64
11:38:00.051211 IP 192.168.4.20 > 192.168.253.1: ICMP echo request, id 3928, seq 211, length 64
11:38:00.051871 IP 192.168.253.1 > 192.168.4.20: ICMP echo reply, id 3928, seq 211, length 64
11:38:01.053130 IP 192.168.4.20 > 192.168.253.1: ICMP echo request, id 3928, seq 212, length 64
11:38:01.053703 IP 192.168.253.1 > 192.168.4.20: ICMP echo reply, id 3928, seq 212, length 64


this works and you can see the replies 


tcpdump -n -i enp0s19 | grep -v ARP
when pinging the google dns server
11:39:12.781653 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 5, length 64
11:39:13.806665 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 6, length 64
11:39:14.830747 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 7, length 64
11:39:15.855205 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 8, length 64
11:39:16.880228 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 9, length 64


you can see the outgoing request but no replies




tcpdump -n -i br0


# tcpdump -n -i br0 | grep 192.168.4
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on br0, link-type EN10MB (Ethernet), capture size 262144 bytes
11:46:26.722381 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 428, length 64
11:46:27.745722 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 429, length 64
11:46:28.769724 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 430, length 64
11:46:29.793575 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 431, length 64
11:46:30.818571 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 432, length 64
11:46:31.841986 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 433, length 64
11:46:32.865680 IP 192.168.4.20 > 8.8.8.8: ICMP echo request, id 3932, seq 434, length 64


tcpdump -n -i ppp0 | grep 8.8.8.8


 shows nothing when pinging from the client on 192.168.4.20


but when pinged from the ubuntu router i get
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on ppp0, link-type LINUX_SLL (Linux cooked), capture size 262144 bytes
11:50:07.271579 IP 8.8.8.8 > INTERNETIP: ICMP echo reply, id 1136, seq 1, length 64
11:50:08.274320 IP 8.8.8.8 > INTERNETIP: ICMP echo reply, id 1136, seq 2, length 64
11:50:09.275580 IP 8.8.8.8 > INTERNETIP: ICMP echo reply, id 1136, seq 3, length 64
11:50:10.276574 IP 8.8.8.8 > INTERNETIP: ICMP echo reply, id 1136, seq 4, length 64
11:50:11.278581 IP 8.8.8.8 > INTERNETIP: ICMP echo reply, id 1136, seq 5, length 64
11:50:12.282094 IP 8.8.8.8 > INTERNETIP: ICMP echo reply, id 1136, seq 6, length 64
11:50:13.284754 IP 8.8.8.8 > INTERNETIP: ICMP echo reply, id 1136, seq 7, length 64
11:50:14.286843 IP 8.8.8.8 > INTERNETIP: ICMP echo reply, id 1136, seq 8, length 64






I have a client which has the ip address of 192.168.4.20 with a default router of 192.168.4.1. This client can ping all of the interfaces on the new router,
and the internet router. It can even access the web pahe of the internet router. So there is some routing going on.


DNS is running on the new router and works fine. the clint on 192.168.4.20 can resolve fine


this isue is the client can not get a response from any device past the internet.
Look to me like the issue between the new router and the internet router


but i'm stuck any ideas ?


Many Thanks
Andrew

---

### Post by Andrew_Welham on 2018-01-28
I've got the answer from [http://www.patrikdufresne.com/en/multiple-subnets-routing-with-dd-wrt/](http://www.patrikdufresne.com/en/multiple-subnets-routing-with-dd-wrt/) after 2 days of work
apparently DD-WRT only nets tot he internet on the first interface, you need to do the following

iptables -t nat -I POSTROUTING -o `get_wanface` -j SNAT --to `nvram get wan_ipaddr`
Click the the &#8220;Run Commands&#8221; button. Then click &#8220;Save Firewall&#8221; to let the router remember about it on the next reboot.

FIXED

---

