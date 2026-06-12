---
title: "No network after upgrading to 8.04"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by geekATlarge on 2008-05-04
I just upgraded to 8.04 and things went well until I tried using the new system. I had no network connections. Reading the forums, others appear to have network type issues but none had resolutions ... If it helps, I fixed my problem.

Problem: no network connection after upgrading 7.10 to 8.04.
Test: you can't access [http://www.ubuntu.com]("http://www.ubuntu.com") while ping shows access like below:
```
$ ping www.ubuntu.com
PING www.ubuntu.com (91.189.94.251) 56(84) bytes of data.
64 bytes from www.ubuntu.com (91.189.94.251): icmp_seq=1 ttl=251 time=61.4 ms
64 bytes from www.ubuntu.com (91.189.94.251): icmp_seq=2 ttl=251 time=61.5 ms
```
Cause: 8.04 activated or changed the configuration of > iptables. After the upgrade, my iptables had the following configuration:
```
 sudo iptables -L

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  .                    anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  .                    anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.3          .                   tcp dpt:domain 
ACCEPT     udp  --  192.168.1.3          .                   udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (1 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSO        all  --  anywhere             anywhere
``` 

Solution: configure your iptables using these references. Note two things. 1) you must sudo to access iptables. 2) you must load the iptables everytime linux/ubuntu boots. Threrefor write the scripts recommended in the first reference.
[URL="http://ubuntuforums.org/showthread.php?t=159661&highlight=HOWTO%3A+Set+custom+firewall+(iptables)+Tips"]
iptables for beginners[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=668148&highlight=HOWTO%3A+Set+custom+firewall+(iptables)+Tips"]
iptables for geeks[/URL]

If you are very desperate, you can open up everything with the following. But you are relying on other sources of firewall to protect your system, because this will open everything. Please follow the recommendations in the references. The following is only a test to verify that your network really does work.
```
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT

```
now verify your connection to [www.ubuntu.com](www.ubuntu.com)

Hope this helps.

Cheers

---

