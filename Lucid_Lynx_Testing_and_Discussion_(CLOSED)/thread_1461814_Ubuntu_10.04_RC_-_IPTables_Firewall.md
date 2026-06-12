---
title: "Ubuntu 10.04 RC - IPTables Firewall"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by EMCGFX on 2010-04-24
Hi, does any one else have this issue with iptables rules. I get my rules flashed every computer reboot. I'm only running custom iptables rules. It worked fine with 9.10. After upgrade to 10.04 RC I get my firewall flashed with some other rules that are not mine.

---

### Post by EMCGFX on 2010-04-25
I did some more digging. This is the rules I get flashed into after boot of Ubuntu 10.04 RC. But not instantly, after 5 minutes. Is this rules familiar to any one ? Does any one know which program doing this ? Kind of scary, ether I got rooted or this RC upgrade is bad.

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  0.0.0.0/8            anywhere            
DROP       all  --  5.0.0.0/8            anywhere            
DROP       all  --  23.0.0.0/8           anywhere            
DROP       all  --  31.0.0.0/8           anywhere            
DROP       all  --  36.0.0.0/8           anywhere            
DROP       all  --  37.0.0.0/8           anywhere            
DROP       all  --  39.0.0.0/8           anywhere            
DROP       all  --  42.0.0.0/8           anywhere            
DROP       all  --  49.0.0.0/8           anywhere            
DROP       all  --  100.0.0.0/8          anywhere            
DROP       all  --  101.0.0.0/8          anywhere            
DROP       all  --  102.0.0.0/8          anywhere            
DROP       all  --  103.0.0.0/8          anywhere            
DROP       all  --  104.0.0.0/8          anywhere            
DROP       all  --  105.0.0.0/8          anywhere            
DROP       all  --  106.0.0.0/8          anywhere            
DROP       all  --  127.0.0.0/8          anywhere            
DROP       all  --  link-local/16        anywhere            
DROP       all  --  176.0.0.0/8          anywhere            
DROP       all  --  177.0.0.0/8          anywhere            
DROP       all  --  179.0.0.0/8          anywhere            
DROP       all  --  181.0.0.0/8          anywhere            
DROP       all  --  185.0.0.0/8          anywhere            
DROP       all  --  192.0.0.0/24         anywhere            
DROP       all  --  192.0.2.0/24         anywhere            
DROP       all  --  198.18.0.0/15        anywhere            
DROP       all  --  198.51.100.0/24      anywhere            
DROP       all  --  203.0.113.0/24       anywhere            
DROP       all  --  224.0.0.0/4          anywhere            
DROP       all  --  240.0.0.0/4          anywhere            
TMP_DROP   all  --  anywhere             anywhere            
TALLOW     all  --  anywhere             anywhere            
TDENY      all  --  anywhere             anywhere            
TGALLOW    all  --  anywhere             anywhere            
TGDENY     all  --  anywhere             anywhere            
DROP       tcp  --  anywhere             anywhere            tcp dpts:loc-srv:netbios-ssn 
DROP       udp  --  anywhere             anywhere            udp dpts:loc-srv:netbios-ssn 
DROP       tcp  --  anywhere             anywhere            tcp dpt:sunrpc 
DROP       udp  --  anywhere             anywhere            udp dpt:sunrpc 
DROP       tcp  --  anywhere             anywhere            tcp dpt:login 
DROP       udp  --  anywhere             anywhere            udp dpt:who 
DROP       tcp  --  anywhere             anywhere            tcp dpt:520 
DROP       udp  --  anywhere             anywhere            udp dpt:route 
DROP       tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
DROP       udp  --  anywhere             anywhere            udp dpt:microsoft-ds 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ms-sql-s 
DROP       udp  --  anywhere             anywhere            udp dpt:ms-sql-s 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ms-sql-m 
DROP       udp  --  anywhere             anywhere            udp dpt:ms-sql-m 
DROP       tcp  --  anywhere             anywhere            tcp dpt:1234 
DROP       udp  --  anywhere             anywhere            udp dpt:1234 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ingreslock 
DROP       udp  --  anywhere             anywhere            udp dpt:ingreslock 
DROP       tcp  --  anywhere             anywhere            tcp dpt:3127 
DROP       udp  --  anywhere             anywhere            udp dpt:3127 
IN_SANITY  all  --  anywhere             anywhere            
FRAG_UDP   all  --  anywhere             anywhere            
PZERO      all  --  anywhere             anywhere            
P2P        all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable limit: avg 30/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp redirect limit: avg 30/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded limit: avg 30/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply limit: avg 30/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp type 30 limit: avg 30/sec burst 5 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request limit: avg 30/sec burst 5 
DROP       tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW 
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  192.168.0.1          anywhere            udp spt:domain dpts:1023:65535 
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp spt:domain dpts:1023:65535 
DROP       tcp  --  anywhere             anywhere            tcp spt:domain dpts:1023:65535 
DROP       udp  --  anywhere             anywhere            udp spt:domain dpts:1023:65535 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1023:65535 dpt:ftp state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            multiport dports ftp,ftp-data state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            multiport dports fsp,20 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ssh dpts:login:65535 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:ssh flags:FIN,SYN,RST,ACK/SYN state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh state ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpts:33434:33534 
DROP       tcp  --  anywhere             anywhere            
DROP       udp  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
DROP       all  --  anywhere             0.0.0.0/8           
DROP       all  --  anywhere             5.0.0.0/8           
DROP       all  --  anywhere             23.0.0.0/8          
DROP       all  --  anywhere             31.0.0.0/8          
DROP       all  --  anywhere             36.0.0.0/8          
DROP       all  --  anywhere             37.0.0.0/8          
DROP       all  --  anywhere             39.0.0.0/8          
DROP       all  --  anywhere             42.0.0.0/8          
DROP       all  --  anywhere             49.0.0.0/8          
DROP       all  --  anywhere             100.0.0.0/8         
DROP       all  --  anywhere             101.0.0.0/8         
DROP       all  --  anywhere             102.0.0.0/8         
DROP       all  --  anywhere             103.0.0.0/8         
DROP       all  --  anywhere             104.0.0.0/8         
DROP       all  --  anywhere             105.0.0.0/8         
DROP       all  --  anywhere             106.0.0.0/8         
DROP       all  --  anywhere             127.0.0.0/8         
DROP       all  --  anywhere             link-local/16       
DROP       all  --  anywhere             176.0.0.0/8         
DROP       all  --  anywhere             177.0.0.0/8         
DROP       all  --  anywhere             179.0.0.0/8         
DROP       all  --  anywhere             181.0.0.0/8         
DROP       all  --  anywhere             185.0.0.0/8         
DROP       all  --  anywhere             192.0.0.0/24        
DROP       all  --  anywhere             192.0.2.0/24        
DROP       all  --  anywhere             198.18.0.0/15       
DROP       all  --  anywhere             198.51.100.0/24     
DROP       all  --  anywhere             203.0.113.0/24      
DROP       all  --  anywhere             224.0.0.0/4         
DROP       all  --  anywhere             240.0.0.0/4         
TMP_DROP   all  --  anywhere             anywhere            
TALLOW     all  --  anywhere             anywhere            
TDENY      all  --  anywhere             anywhere            
TGALLOW    all  --  anywhere             anywhere            
TGDENY     all  --  anywhere             anywhere            
DROP       tcp  --  anywhere             anywhere            tcp dpts:loc-srv:netbios-ssn 
DROP       udp  --  anywhere             anywhere            udp dpts:loc-srv:netbios-ssn 
DROP       tcp  --  anywhere             anywhere            tcp dpt:sunrpc 
DROP       udp  --  anywhere             anywhere            udp dpt:sunrpc 
DROP       tcp  --  anywhere             anywhere            tcp dpt:login 
DROP       udp  --  anywhere             anywhere            udp dpt:who 
DROP       tcp  --  anywhere             anywhere            tcp dpt:520 
DROP       udp  --  anywhere             anywhere            udp dpt:route 
DROP       tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
DROP       udp  --  anywhere             anywhere            udp dpt:microsoft-ds 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ms-sql-s 
DROP       udp  --  anywhere             anywhere            udp dpt:ms-sql-s 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ms-sql-m 
DROP       udp  --  anywhere             anywhere            udp dpt:ms-sql-m 
DROP       tcp  --  anywhere             anywhere            tcp dpt:1234 
DROP       udp  --  anywhere             anywhere            udp dpt:1234 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ingreslock 
DROP       udp  --  anywhere             anywhere            udp dpt:ingreslock 
DROP       tcp  --  anywhere             anywhere            tcp dpt:3127 
DROP       udp  --  anywhere             anywhere            udp dpt:3127 
OUT_SANITY  all  --  anywhere             anywhere            
FRAG_UDP   all  --  anywhere             anywhere            
PZERO      all  --  anywhere             anywhere            
P2P        all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:whois 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:20 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:fsp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     icmp --  anywhere             anywhere            limit: avg 30/sec burst 5 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:1024:65535 state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:1024:65535 state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             192.168.0.1         udp spts:1023:65535 dpt:domain 
ACCEPT     tcp  --  anywhere             192.168.0.1         tcp spts:1023:65535 dpt:domain 
ACCEPT     udp  --  anywhere             192.168.0.1         udp spts:1023:65535 dpt:domain 
ACCEPT     tcp  --  anywhere             192.168.0.1         tcp spts:1023:65535 dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ftp dpts:1023:65535 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            multiport dports ftp,ftp-data state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            multiport dports fsp,20 state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpts:33434:33534 
DROP       tcp  --  anywhere             anywhere            
DROP       udp  --  anywhere             anywhere            
DROP       all  --  anywhere             anywhere            

Chain FRAG_UDP (2 references)
target     prot opt source               destination         
DROP       udp  -f  anywhere             anywhere            

Chain IN_SANITY (1 references)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN 
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN,RST 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,RST/FIN,RST 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,ACK/FIN 
DROP       tcp  --  anywhere             anywhere            tcp flags:ACK,URG/URG 
DROP       tcp  --  anywhere             anywhere            tcp flags:PSH,ACK/PSH 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,PSH,URG 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,ACK,URG 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN 

Chain OUT_SANITY (1 references)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN 
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN,RST 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,RST/FIN,RST 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,ACK/FIN 
DROP       tcp  --  anywhere             anywhere            tcp flags:PSH,ACK/PSH 
DROP       tcp  --  anywhere             anywhere            tcp flags:ACK,URG/URG 

Chain P2P (2 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            tcp dpt:kazaa reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spt:kazaa dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:1024:65534 dpt:kazaa reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spt:kazaa dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:2323 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spt:2323 dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:1024:65534 dpt:2323 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spt:2323 dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spts:1024:65534 dpts:4660:4678 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spts:4660:4678 dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:1024:65534 dpts:4660:4678 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:4660:4678 dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:6257 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spt:6257 dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:1024:65534 dpt:6257 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spt:6257 dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:6699 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spt:6699 dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:1024:65534 dpt:6699 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spt:6699 dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:gnutella-svc reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spt:gnutella-svc dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:1024:65534 dpt:gnutella-svc reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spt:gnutella-svc dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:gnutella-rtr reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spt:gnutella-rtr dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:1024:65534 dpt:gnutella-rtr reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spt:gnutella-rtr dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spts:1024:65534 dpts:6881:6889 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spts:6881:6889 dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:1024:65534 dpts:6881:6889 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:6881:6889 dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:gnutella-svc reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spt:gnutella-svc dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:1024:65534 dpt:gnutella-svc reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spt:gnutella-svc dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:7778 reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp spt:7778 dpts:1024:65534 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spts:1024:65534 dpt:7778 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp spt:7778 dpts:1024:65534 reject-with icmp-port-unreachable 

Chain PROHIBIT (0 references)
target     prot opt source               destination         
REJECT     all  --  anywhere             anywhere            reject-with icmp-host-prohibited 

Chain PZERO (2 references)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere            tcp dpt:0 
DROP       udp  --  anywhere             anywhere            udp dpt:0 
DROP       tcp  --  anywhere             anywhere            tcp spt:0 
DROP       udp  --  anywhere             anywhere            udp spt:0 

Chain RESET (0 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 

Chain TALLOW (2 references)
target     prot opt source               destination         

Chain TDENY (2 references)
target     prot opt source               destination         

Chain TGALLOW (2 references)
target     prot opt source               destination         

Chain TGDENY (2 references)
target     prot opt source               destination         

Chain TMP_DROP (2 references)
target     prot opt source               destination         

```

---

### Post by EMCGFX on 2010-04-25
Never mind. I forgot I've installed APF firewall script. Removed it.

Here is what I did to remove it;

/etc/init.d/iptables stop
rm -Rfv /etc/apf
rm -fv /etc/cron.daily/fw
chkconfig apf off
rm -fv /etc/init.d/apf

---

