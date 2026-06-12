---
title: "Iptables problem"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by Turtle.net on 2005-04-23
Hi,
I want to set-up my firewall using iptables.
Different howtos are very interesting (especialy on gentoo forums).
But I do not know how I can launch iptables with my rules.
Under Gentoo I just have to verify ```
/etc/init.d/iptables start
```
But in my Hoary Ubuntu box I do not find /etc/init.d/iptables   :???: 

Any help ??

---

### Post by ubuntu_demon on 2005-04-23
[QUOTE=Turtle.net]Hi,
I want to set-up my firewall using iptables.
Different howtos are very interesting (especialy on gentoo forums).
But I do not know how I can launch iptables with my rules.
Under Gentoo I just have to verify ```
/etc/init.d/iptables start
```
But in my Hoary Ubuntu box I do not find /etc/init.d/iptables   :???: 

Any help ??[/QUOTE]
 just put all your iptables in a script for example :

```

#!/bin/bash

# Flushing all tables
iptables -F

### filter
# I only filter INPUT OUTPUT and FORWARD are accepted by default

iptables -t filter -P INPUT DROP
iptables -t filter -P OUTPUT ACCEPT
iptables -t filter -P FORWARD ACCEPT

# allow local loopback connections
iptables -t filter -A INPUT -i lo -j ACCEPT

# drop INVALID connections
iptables -t filter -A INPUT   -m state --state INVALID -j DROP
iptables -t filter -A OUTPUT  -m state --state INVALID -j DROP
iptables -t filter -A FORWARD -m state --state INVALID -j DROP

# allow all established and related
iptables -t filter -A INPUT   -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t filter -A OUTPUT  -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t filter -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

# allow connections to my ISP's DNS servers
iptables -t filter -A INPUT -s 213.73.255.52 -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -j ACCEPT 
iptables -t filter -A INPUT -s 213.73.255.52 -p udp -j ACCEPT 
iptables -t filter -A INPUT -s 213.132.189.250 -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -j ACCEPT 
iptables -t filter -A INPUT -s 213.132.189.250 -p udp -j ACCEPT 
iptables -t filter -A INPUT -s 213.73.255.53 -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -j ACCEPT 
iptables -t filter -A INPUT -s 213.73.255.53 -p udp -j ACCEPT 

# the only ICMP that's accepted is ping but there's a rate limit to prevent DDOS
iptables -t filter -A INPUT -p icmp --icmp-type echo-request -m limit --limit 10/sec -j ACCEPT

#open ports 22 = ssh, 4662,4672,4675 = amule , 6881-6889 = bittorrent
iptables -t filter -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT 
iptables -t filter -A INPUT -p tcp -m tcp --dport 4662 -j ACCEPT 
iptables -t filter -A INPUT -p udp -m udp --dport 4672 -j ACCEPT
iptables -t filter -A INPUT -p udp -m udp --dport 4675 -j ACCEPT
iptables -t filter -A INPUT -p tcp -m tcp --dport 6881:6889 -j ACCEPT 

#samba (only connections from lan are accepted)
iptables -t filter -A INPUT -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 137:139 -j ACCEPT 
iptables -t filter -A INPUT -s 192.168.0.0/255.255.255.0 -p udp -m udp --dport 137:139 -j ACCEPT 
iptables -t filter -A INPUT -s 192.168.0.0/255.255.255.0 -p tcp -m tcp --dport 445 -j ACCEPT 
iptables -t filter -A INPUT -s 192.168.0.0/255.255.255.0 -p udp -m udp --dport 445 -j ACCEPT 

# log all other attempted in going connections
iptables -t filter -A INPUT -j LOG

```

after this do  the following :

$chmod +x scriptname
$sudo ./scriptname

If you want the script to be automaticaly loaded you should put in /etc/init.d by :
$ sudo cp scriptname /etc/init.d

now to enable it :

$sudo update-rc.d scriptname defaults

---

### Post by elysium444 on 2006-12-19
[COLOR="Sienna"][SIZE="2"]I am having the same problem...I cant fix the NAT problem in azureus.
I tried the script and didn't work than I made some changes:[/SIZE][/COLOR]

[COLOR="Black"][SIZE="1"][I]#!/bin/bash

# Flushing all tables
iptables -F

### filter
# I only filter INPUT OUTPUT and FORWARD are accepted by default
iptables -t filter -P INPUT DROP
iptables -t filter -P OUTPUT ACCEPT
iptables -t filter -P FORWARD ACCEPT

# allow local loopback connections
iptables -t filter -A INPUT -i lo -j ACCEPT

# drop INVALID connections
iptables -t filter -A INPUT   -m state --state INVALID -j DROP
iptables -t filter -A OUTPUT  -m state --state INVALID -j DROP
iptables -t filter -A FORWARD -m state --state INVALID -j DROP

# allow all established and related
iptables -t filter -A INPUT   -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t filter -A OUTPUT  -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -t filter -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

# allow connections to my ISP's DNS servers
iptables -t filter -A INPUT -s 80.91.112.2 -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -j ACCEPT 
iptables -t filter -A INPUT -s 80.91.112.2 -p udp -j ACCEPT 
iptables -t filter -A INPUT -s 213.149.114.3 -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -j ACCEPT 
iptables -t filter -A INPUT -s 213.149.114.3 -p udp -j ACCEPT 
iptables -t filter -A INPUT -s 217.24.240.4 -p tcp -m tcp ! --tcp-flags SYN,RST,ACK SYN -j ACCEPT 
iptables -t filter -A INPUT -s 217.24.240.4 -p udp -j ACCEPT 

# the only ICMP that's accepted is ping but there's a rate limit to prevent DDOS
iptables -t filter -A INPUT -p icmp --icmp-type echo-request -m limit --limit 10/sec -j ACCEPT

#open ports 22 = ssh, 4662,4672,4675 = amule , 6881-6889 = bittorrent
iptables -t filter -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT 
iptables -t filter -A INPUT -p tcp -m tcp --dport 4662 -j ACCEPT 
iptables -t filter -A INPUT -p udp -m udp --dport 4672 -j ACCEPT
iptables -t filter -A INPUT -p udp -m udp --dport 4675 -j ACCEPT
iptables -t filter -A INPUT -p tcp -m tcp --dport 6881:6889 -j ACCEPT 


# log all other attempted in going connections
iptables -t filter -A INPUT -j LOG
#show info
iptables -L[/I][/SIZE][/COLOR]


[COLOR="Sienna"][SIZE="2"]
And this pop out in the terminal:[/SIZE][/COLOR]
[SIZE="1"][COLOR="Black"]root@elysium_444[/etc]# /home/elysium444/script/nat2
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     0    --  anywhere             anywhere
DROP       0    --  anywhere             anywhere            state INVALID
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  dns.abissnet.com.al  anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  dns.abissnet.com.al  anywhere
ACCEPT     tcp  --  213.149.114.3        anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  213.149.114.3        anywhere
ACCEPT     tcp  --  temp2.atnet.com.al   anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  temp2.atnet.com.al   anywhere
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request limit: avg 10/sec burst 5
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4662
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4672
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4675
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889
LOG        0    --  anywhere             anywhere            LOG level warning

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
DROP       0    --  anywhere             anywhere            state INVALID
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
DROP       0    --  anywhere             anywhere            state INVALID
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED
root@elysium_444[/etc]#

[/COLOR][/SIZE]

I still got the nat problem how can I make azureus work I have been searchin all the week and couldn't find nothing.
please help me.

---

### Post by elysium444 on 2006-12-19
I tried this:
root@elysium_444[/etc]# iptables -F
root@elysium_444[/etc]# /home/elysium444/script/nat2
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     0    --  anywhere             anywhere
DROP       0    --  anywhere             anywhere            state INVALID
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  dns.abissnet.com.al  anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  dns.abissnet.com.al  anywhere
ACCEPT     tcp  --  213.149.114.3        anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  213.149.114.3        anywhere
ACCEPT     tcp  --  temp2.atnet.com.al   anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  temp2.atnet.com.al   anywhere
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request limit: avg 10/sec burst 5
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4662
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4672
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4675
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889
LOG        0    --  anywhere             anywhere            LOG level warning

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
DROP       0    --  anywhere             anywhere            state INVALID
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
DROP       0    --  anywhere             anywhere            state INVALID
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED

---

### Post by Rookie- on 2006-12-19
Dont forget to tell the script where iptables is, also, dont forget to tell the script what eth is and what ip each nic has.

---

