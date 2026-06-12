---
title: "Network throughput"
date: 2009-05-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2009-05-23
Network throughput is very very weak. I am only getting, at most, 50 kb/s down.

```
*-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@
       logical name: wmaster0
       version: 01
       serial: 
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.2 latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn
```

I am connected to a lynksys wrt 160n.

---

### Post by taavikko on 2009-05-23
through what? Internal transfer speeds, or from internet?
It makes hardly no difference what hardware you have, when ISP have set your donwload speed to 512kb (roughly 50KiB) (I may have again mixed the acronyms for the byte bit etc)

---

### Post by Kareeser on 2009-05-23
How are you measuring your throughput? Through apt-get? Some mirrors are throttled to conserve bandwidth, and you won't get an accurate reading.

---

### Post by tad1073 on 2009-05-23
Watching my speeds when I run an update, download a package, internet pages, you name it. Before, my transfer rates would range between 150 kb/s and 300 kb/s. I know its not ubuntu package servers or their web sites because my transfer rates while using W7 are normal, between 300 kb/s and 500 kb/s.

Last night I downloaded something from Nvidia and had transfer rates or over 600 kb/s.

I'm thinking it may be the kernel module or network manager, but I really don't have a clue because I am not a developer.

---

### Post by tad1073 on 2009-05-24
bump

---

### Post by cariboo on 2009-05-24
If you have a second computer you can use iperf to check your actual transfer rates. Run iperf as a server on one computer and then run iperf on the other computer. this will give you a transfer rate that makes sense instead judging by the transfer from the internet. This is the result I get using the computer I'm on and my server:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.101 port 49523 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    113 MBytes  94.4 Mbits/sec
```

iperf is available in the repositories.

---

### Post by tad1073 on 2009-05-25
I figured out what the problem is. The router I use is a wireless N router that is capable of G+N/mixed mode. The problem is wireless N. Linux has poor support for wireless N.

When I switched to G only mode my speeds doubled, if not tripled.

---

