---
title: "Need help understanding PSAD result"
date: 2017-10-29
forum: MINT
---

### Post by linuxyogi on 2017-10-29
Hi,

Using 16.04. I am connected to the internet directly without a router. I have configured PSAD by following[ this guide]("https://komunity.komand.com/learn/article/network-security/how-to-install-and-use-psad-ids-on-ubuntu-linux/"). 

Please help me understand the output of

```
$ sudo psad -S
[-] psad: pid file /var/run/psad/psadwatchd.pid does not exist for psadwatchd on mint
[+] psad (pid: 20085)  %CPU: 0.0  %MEM: 0.6
    Running since: Sun Oct 29 17:38:21 2017
    Command line arguments: [none specified]
    Alert email address(es): mymail@gmail.com

[+] Version: psad v2.2.3

[+] Top 50 signature matches:
        [NONE]

[+] Top 25 attackers:
      172.16.197.127  DL: 2, Packets: 31, Sig count: 0
      172.16.197.184  DL: 2, Packets: 20, Sig count: 0
      172.16.197.186  DL: 2, Packets: 22, Sig count: 0
      172.16.197.212  DL: 2, Packets: 15, Sig count: 0
      172.16.197.7    DL: 2, Packets: 17, Sig count: 0
      10.18.37.12     DL: 1, Packets: 12, Sig count: 0
      172.16.197.67   DL: 1, Packets: 5, Sig count: 0
      172.16.197.99   DL: 1, Packets: 9, Sig count: 0

[+] Top 20 scanned ports:
        [NONE]

[+] iptables log prefix counters:
      "[UFW BLOCK]": 23

    Total protocol packet counters:

[+] IP Status Detail:

SRC:  172.16.197.127, DL: 2, Dsts: 1, Pkts: 31, Total protocols: 1, Unique sigs: 0, Email alerts: 8, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.184, DL: 2, Dsts: 1, Pkts: 20, Total protocols: 1, Unique sigs: 0, Email alerts: 8, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.186, DL: 2, Dsts: 1, Pkts: 22, Total protocols: 1, Unique sigs: 0, Email alerts: 7, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.212, DL: 2, Dsts: 1, Pkts: 15, Total protocols: 1, Unique sigs: 0, Email alerts: 7, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.7, DL: 2, Dsts: 1, Pkts: 17, Total protocols: 1, Unique sigs: 0, Email alerts: 9, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  10.18.37.12, DL: 1, Dsts: 1, Pkts: 12, Total protocols: 1, Unique sigs: 0, Email alerts: 8

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.67, DL: 1, Dsts: 1, Pkts: 5, Total protocols: 1, Unique sigs: 0, Email alerts: 1, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.99, DL: 1, Dsts: 1, Pkts: 9, Total protocols: 1, Unique sigs: 0, Email alerts: 4, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

    Total scan sources: 8
    Total scan destinations: 1

[+] These results are available in: /var/log/psad/status.out


```

172.16.197.XX is the WAN segment of my cable ISP.

---

### Post by linuxyogi on 2017-10-29
```
$ sudo psad -S
[sudo] password for mint: 
[-] psad: pid file /var/run/psad/psadwatchd.pid does not exist for psadwatchd on mint
[+] psad (pid: 20085)  %CPU: 0.0  %MEM: 0.6
    Running since: Sun Oct 29 17:38:21 2017
    Command line arguments: [none specified]
    Alert email address(es): mymail@gmail.com

[+] Version: psad v2.2.3

[+] Top 50 signature matches:
        [NONE]

[+] Top 25 attackers:
      172.16.197.127  DL: 3, Packets: 167, Sig count: 0
      10.18.37.12     DL: 2, Packets: 23, Sig count: 0
      172.16.197.184  DL: 2, Packets: 98, Sig count: 0
      172.16.197.186  DL: 2, Packets: 52, Sig count: 0
      172.16.197.212  DL: 2, Packets: 62, Sig count: 0
      172.16.197.218  DL: 2, Packets: 22, Sig count: 0
      172.16.197.7    DL: 2, Packets: 33, Sig count: 0
      172.16.197.82   DL: 2, Packets: 17, Sig count: 0
      172.16.197.99   DL: 2, Packets: 50, Sig count: 0
      172.16.197.108  DL: 1, Packets: 7, Sig count: 0
      172.16.197.195  DL: 1, Packets: 13, Sig count: 0
      172.16.197.65   DL: 1, Packets: 11, Sig count: 0
      172.16.197.67   DL: 1, Packets: 6, Sig count: 0

[+] Top 20 scanned ports:
        [NONE]

[+] iptables log prefix counters:
      "[UFW BLOCK]": 115

    Total protocol packet counters:

[+] IP Status Detail:

SRC:  172.16.197.127, DL: 3, Dsts: 1, Pkts: 167, Total protocols: 1, Unique sigs: 0, Email alerts: 58, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  10.18.37.12, DL: 2, Dsts: 1, Pkts: 23, Total protocols: 1, Unique sigs: 0, Email alerts: 18

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.184, DL: 2, Dsts: 1, Pkts: 98, Total protocols: 1, Unique sigs: 0, Email alerts: 52, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.186, DL: 2, Dsts: 1, Pkts: 52, Total protocols: 1, Unique sigs: 0, Email alerts: 19, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.212, DL: 2, Dsts: 1, Pkts: 62, Total protocols: 1, Unique sigs: 0, Email alerts: 38, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.218, DL: 2, Dsts: 1, Pkts: 22, Total protocols: 1, Unique sigs: 0, Email alerts: 11, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.7, DL: 2, Dsts: 1, Pkts: 33, Total protocols: 1, Unique sigs: 0, Email alerts: 19, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.82, DL: 2, Dsts: 1, Pkts: 17, Total protocols: 1, Unique sigs: 0, Email alerts: 9, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.99, DL: 2, Dsts: 1, Pkts: 50, Total protocols: 1, Unique sigs: 0, Email alerts: 34, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.108, DL: 1, Dsts: 1, Pkts: 7, Total protocols: 1, Unique sigs: 0, Email alerts: 2, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.195, DL: 1, Dsts: 1, Pkts: 13, Total protocols: 1, Unique sigs: 0, Email alerts: 7, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.65, DL: 1, Dsts: 1, Pkts: 11, Total protocols: 1, Unique sigs: 0, Email alerts: 6, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

SRC:  172.16.197.67, DL: 1, Dsts: 1, Pkts: 6, Total protocols: 1, Unique sigs: 0, Email alerts: 2, Local IP

    DST: 224.0.0.251
        Total scanned IP protocols: 1, Chain: INPUT, Intf: enp2s0

    Total scan sources: 13
    Total scan destinations: 1

[+] These results are available in: /var/log/psad/status.out

```


Here is the same test again

---

### Post by linuxyogi on 2017-10-30
Any ideas ?

---

### Post by linuxyogi on 2017-10-30
Bump

---

### Post by Perfect Storm on 2017-10-31
Moved to Mint subforum.

---

