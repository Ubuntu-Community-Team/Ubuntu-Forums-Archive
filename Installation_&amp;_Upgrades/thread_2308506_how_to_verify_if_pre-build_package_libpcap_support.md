---
title: "how to verify if pre-build package libpcap support nflog interface?"
date: 2016-01-03
forum: Installation &amp; Upgrades
---

### Post by darkblue2000 on 2016-01-03
hello,

My OS is ubuntu 14.04.03

I am going to utilize tcpdump to capture package from nfnetlink_log(nflog).but when I issue "tcpdump -D", there is not nflog options, they look like this:


chenrui@gateway-3:~/libpcap-1.5.3$ sudo tcpdump -D
1.eth0
2.nfqueue (Linux netfilter queue (NFQUEUE) interface)
3.eth1
4.any (Pseudo-device that captures on all interfaces)
5.lo


the debian wheezy's version is OK, like this:


chenrui@d7-64-gw-1:/tmp/libpcap-1.3.0$ sudo tcpdump -D
1.eth0
2.nflog (Linux netfilter log (NFLOG) interface)
3.any (Pseudo-device that captures on all interfaces)
4.lo

it should be ubuntu's libpcap compile options problem. how to enable pcap netfilter support and re-compile libpcap?

---

