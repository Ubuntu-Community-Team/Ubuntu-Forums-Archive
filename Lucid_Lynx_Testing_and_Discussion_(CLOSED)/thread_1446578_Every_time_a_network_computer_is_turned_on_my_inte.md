---
title: "Every time a network computer is turned on my internet dissconnect"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-04
i have a crossover  home network and every time the second computer is turned on my Internet  connection disconnect and i need to reconnect and then i have Internet on computers why does this happen and how can i fix it?

thanks in advance.

---

### Post by aviramof on 2010-04-05
doesn't anyone has an idea?

---

### Post by cariboo on 2010-04-05
It sounds like two systems may have the same ip address.

---

### Post by aviramof on 2010-04-05
it's a home network with share internet connection my computer the main computer is 192.168.137.1 and the other is 192.168.137.2 the leagel ip is dynamic but it's the same in bote computers of course.
 
the problem is that when 192.168.137.2 connect to the home network the internet connection on my ubuntu dissconnect and it's very strange.
 
i have two network cards eth0 and eth1 and pppoe the strange way that ubuntu connect to the internet make it impossible for me to know in what
 
eth device the internet connection is using or the network connection is using you can never tell if it's eth0 or eth1 it's like in xp when you set an 
 
an ip address to spesifce device in ubuntu it's more like luck if you can share internet at all because if you try to assign it by mac address it's not 
 
always working well.

---

### Post by lisati on 2010-04-05
> **aviramof said:**
> i have a crossover  home network and every time the second computer is turned on my Internet  connection disconnect and i need to reconnect and then i have Internet on computers why does this happen and how can i fix it?

thanks in advance.

I'm not sure what you mean by a "crossover network". Is your second computer plugged into your first computer to share its internet connection?

Edit: posted before I saw the previous post.

---

### Post by aviramof on 2010-04-05
exceclly read what i edited in the previous reply i'm using a crossover cable in my computer there are two network cards one for the internet the other for the home netwrok but managing two eth devices in ubuntu is quite coplicated and confusing.

---

### Post by cariboo on 2010-04-05
The second network card and the other networked computer have to be in a different netblock form the main  network interface eg: 

If eth0 in the internet connected system is 192.168.1.100, the second interface eth1 should be 192.168.2.100, and the other system on the network could be 192.168.2.101

---

### Post by aviramof on 2010-04-05
first of all i'm using eth0 as the home network card this is the one who is on the motherboard a rhine ii card eth1 is a pci realtek network card and this is the one 
i'm using for internet connection now eth1 get it's ip address from dhcp via the isp
eth0 i set as 192.168.137.1 because that is what windows 7 likes it's the defualt number he gives and i gave the xp computer 192.168.137.2 the leagal ip is class b 
not c and begin with 89 not 192 or anything near that so there shouldn't be a problem 
at all.
 
for my ics i'm using this commands:
#!/bin/sh
iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward
 
in the file /etc/network/if-up.d/netsharing that someone here told me to use maybe this command don't work very well with lucid they are after all came from karma guide.

---

### Post by alphacrucis2 on 2010-04-05
> **aviramof said:**
> first of all i'm using eth0 as the home network card this is the one who is on the motherboard a rhine ii card eth1 is a pci realtek network card and this is the one 
i'm using for internet connection now eth1 get it's ip address from dhcp via the isp
eth0 i set as 192.168.137.1 because that is what windows 7 likes it's the defualt number he gives and i gave the xp computer 192.168.137.2 the leagal ip is class b 
not c and begin with 89 not 192 or anything near that so there shouldn't be a problem 
at all.
 
for my ics i'm using this commands:
#!/bin/sh
iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward
 
in the file /etc/network/if-up.d/netsharing that someone here told me to use maybe this command don't work very well with lucid they are after all came from karma guide.

What have you got in /etc/sysctl.conf ?

---

### Post by aviramof on 2010-04-05
```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1

net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
```

---

### Post by JEREMIAHBARLOW on 2010-04-05
Hi all. 

Did you find a solution?

I have a Verizon Wireless 595 Air card as my Internet source.  I went through the process of doing Internet Connection Sharing (ICS) found on some of the other forums.  And it worked a little but stopped working properly.  Every time I use my computer (Ubuntu 9.10 on a Dell D620) only then the internet just works all the time, but if I boot up a Windows XP virtual machine or connect any other computer to the network and put the smallest LOAD to the internet then my Air Card, disconnects and then connects, and disconnects and connects.  Off and on and off and on.  Surely it is something to do with the ICS part of the routing.  It only happens under a internet load from a secondary computers.

I wish ICS was as easy as in windows :(

Thanks,
Jer

---

### Post by doas777 on 2010-04-05
> **aviramof said:**
> i have a crossover  home network and every time the second computer is turned on my Internet  connection disconnect and i need to reconnect and then i have Internet on computers why does this happen and how can i fix it?

thanks in advance.

please describe what you mean by this: "crossover  home network". are you saying that your network is wired with crossover cable?

i have to agree, it sounds like there is some confusion with conflicting IPs or MACs. 
if you run 
```

ifconfig

```on all the linux boxes, and 
```
ipconfig /all
``` on any windows boxes, what IP (Inet) addresses are you showing?

Edit: man this thread is fast. can't ask a question before it is nullified...

---

### Post by aviramof on 2010-04-05
I really didn't understand your last comment but any way this is my ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:16:17:ca:28:0c  
          inet addr:192.168.137.1  Bcast:192.168.137.255   Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:feca:280c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3736 (3.7 KB)  TX bytes:21266 (21.2 KB)
          Interrupt:23 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1d:0f:ff:c7:c3  
          inet6 addr: fe80::21d:fff:feff:c7c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:990 errors:0 dropped:0 overruns:0 frame:0
          TX packets:918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:800111 (800.1 KB)  TX bytes:138611 (138.6 KB)
          Interrupt:18 Base address:0xf800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9749 (9.7 KB)  TX bytes:9749 (9.7 KB)

ppp0      Link encap:Point-to-Point  Protocol  
          inet addr:93.173.156.11  P-t-P:93.173.128.1   Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:76326 (76.3 KB)  TX bytes:3373 (3.3 KB)
```the legal ip address would change once i disconnect and this is my ipconfig /all
  
```

Windows IP Configuration 
 
        Host Name . . . . . . . . . . . . : XPHOME 
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Mixed 
        IP Routing Enabled. . . . . . . . : No 
        WINS Proxy Enabled. . . . . . . . : No 
 
Ethernet adapter Local Area Connection: 
 
        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : SiS 900 PCI Fast Ethernet  Adapter 
        Physical Address. . . . . . . . . : 00-E0-18-07-3C-3F 
        Dhcp Enabled. . . . . . . . . . . : No 
        IP Address. . . . . . . . . . . . : 192.168.137.2 
        Subnet Mask . . . . . . . . . . . : 255.255.255.0 
        Default Gateway . . . . . . . . . : 192.168.137.1 
        DNS Servers . . . . . . . . . . . : 194.90.1.5 
                                            212.143.212.143
```

Maybe now we could solve all this networks problems once and for all.

Thanks in advance.

---

### Post by JEREMIAHBARLOW on 2010-04-05
In my case, I know for sure it is not an IP nor Mac address issue.  I have been building networks for 15 years now.  I just am new to Linux and Ubuntu 9.10.

I am supposing it is something to do with the command that makes ICS work and how it communicates to the network card driver on the outgoing network card. 

I have removed the device under Network Connections and re-set-it-up.  Same issue comes back when I put a load from a different network computer.  It works for a few seconds and then, off and on.. (I know the reason it turns back on is because I set that network card to connect automatically)  But why does it keep dropping?

Very strange if you ask me.  Help Help, how would someone go about recreating this issue or even process of elimination? 

-Jer

---

### Post by aviramof on 2010-04-06
i think we need to check every part of the ics commands all the -m -i -j and etc and see if we still need it and see if removing it improves the connection:

iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m conntrack   --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j   ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward

---

