---
title: "iptables load balance"
date: 2018-03-07
forum: MINT
---

### Post by faustf2 on 2018-03-07
hi guys
i try to set a load balance  with 2 isp by wifi,  this is my scenario: 
pc with  Linux Mint 18.3 Sylvia 64-bit
Kernel Linux 4.13.0-36-generic x86_64
mate 18

i have  first wireless  wlp6s0 in 192.168.0.52
and second wireless  wlp8s0  in 192.168.1.18 

first controll the rule of iptables with this command  sudo iptables -L
return this:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

 classical vanilla configuration

i try to follow  this  tutorial
[https://serverfault.com/questions/93678/load-balancing-nat-ing-multiple-isp-connections-on-linux](https://serverfault.com/questions/93678/load-balancing-nat-ing-multiple-isp-connections-on-linux)
but  when i try to run  with sudo this code
```
ip route show table main | grep -Ev '^default' \
   | while read ROUTE ; do
     ip route add table ISP1 $ROUTE
done

```
return always 
RTNETLINK answers: Operation not permitted
RTNETLINK answers: Operation not permitted

why if  i run with sudo!!!
anyone  can help me ?? 
thankz at all

---

### Post by wildmanne39 on 2018-03-07
*Thread moved to **MINT, a more appropriate forum**.*

---

### Post by faustf2 on 2018-03-08
in mint forum  not  have reply therfore i write here

---

### Post by wildmanne39 on 2018-03-08
You can bump your thread once every twelve hours so people will see it.

---

