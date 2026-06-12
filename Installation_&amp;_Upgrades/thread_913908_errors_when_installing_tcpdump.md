---
title: "errors when installing tcpdump"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by CricketLong on 2008-09-08
./../libpcap-0.9.4/libpcap.a 
./../libpcap-0.9.4/libpcap.a(pcap.o): In function `pcap_datalink_name_to_val':
pcap.c:(.text+0x140): multiple definition of `pcap_datalink_name_to_val'
dlnames.o:dlnames.c:(.text+0xa0): first defined here
./../libpcap-0.9.4/libpcap.a(pcap.o): In function `pcap_datalink_val_to_name':
pcap.c:(.text+0x1b0): multiple definition of `pcap_datalink_val_to_name'
dlnames.o:dlnames.c:(.text+0x0): first defined here
./../libpcap-0.9.4/libpcap.a(pcap.o): In function `pcap_datalink_val_to_description':
pcap.c:(.text+0x200): multiple definition of `pcap_datalink_val_to_description'
dlnames.o:dlnames.c:(.text+0x50): first defined here
./../libpcap-0.9.4/libpcap.a(pcap.o): In function `pcap_list_datalinks':
pcap.c:(.text+0x720): multiple definition of `pcap_list_datalinks'
datalinks.o:datalinks.c:(.text+0x0): first defined here
tcpdump.o: In function `main':
tcpdump.c:(.text+0xb68): undefined reference to `pcap_debug'
./../libpcap-0.9.4/libpcap.a(gencode.o): In function `pcap_compile':
gencode.c:(.text+0x641): undefined reference to `pcap_parse'
collect2: ld returned 1 exit status
make: *** [tcpdump] Error 1


how can I do?

---

### Post by Partyboi2 on 2008-09-08
You can install it from the ubuntu repos unless you need to compile it for some reason. In a terminal
```
sudo apt-get install tcpdump
```

---

