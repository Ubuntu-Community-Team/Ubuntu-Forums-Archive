---
title: "DNS caching &quot;no servers could be reached&quot;"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by kgordon-0 on 2014-06-08
I have smoothwall between the network and the internet in which I set-up: Network -> Incoming and included port 53. DNS can't get through. Any comments would be appreciated.
```

dig ubuntu.com
; <<>> DiG 9.9.5-3-Ubuntu <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached
[EMAIL="root@kgwebsite:/"]root@kgwebsite:/[/EMAIL]# lsof -Pn -iUDP:53
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
named   4189 bind  512u  IPv6  49653      0t0  UDP *:53
named   4189 bind  513u  IPv6  49653      0t0  UDP *:53
named   4189 bind  514u  IPv4  49658      0t0  UDP 127.0.0.1:53
named   4189 bind  515u  IPv4  49658      0t0  UDP 127.0.0.1:53
named   4189 bind  516u  IPv4  49660      0t0  UDP 192.168.2.3:53
named   4189 bind  517u  IPv4  49660      0t0  UDP 192.168.2.3:53
[EMAIL="root@kgwebsite:/"]root@kgwebsite:/[/EMAIL]# lsof -Pn -iTCP:53
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
named   4189 bind   20u  IPv6  49654      0t0  TCP *:53 (LISTEN)
named   4189 bind   21u  IPv4  49659      0t0  TCP 127.0.0.1:53 (LISTEN)
named   4189 bind   22u  IPv4  49661      0t0  TCP 192.168.2.3:53 (LISTEN)
[EMAIL="root@kgwebsite:/"]root@kgwebsite:/[/EMAIL]# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=54 time=41.4 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=54 time=41.8 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=54 time=42.4 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=54 time=42.8 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=54 time=42.2 ms
^C
--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 41.452/42.183/42.881/0.501 ms
[EMAIL="root@kgwebsite:/"]root@kgwebsite:/[/EMAIL]# ping ubuntu.com
PING ubuntu.com (91.189.94.156) 56(84) bytes of data.
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=1 ttl=51 time=293 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=2 ttl=51 time=300 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=3 ttl=51 time=292 ms
64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=4 ttl=51 time=299 ms
^C
--- ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 292.365/296.436/300.560/3.587 ms

```

---

### Post by kgordon-0 on 2014-06-09
What made the difference: I don't know:
root@kgwebsite:/# nslookup paradise.net.nz
Server:         127.0.0.1
Address:        127.0.0.1#53
Non-authoritative answer:
Name:   paradise.net.nz
Address: 203.96.152.127
root@kgwebsite:/# dig paradise.net.nz
; <<>> DiG 9.9.5-3-Ubuntu <<>> paradise.net.nz
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14936
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 13, ADDITIONAL: 1
;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;paradise.net.nz.               IN      A
;; ANSWER SECTION:
paradise.net.nz.        172702  IN      A       203.96.152.127
;; AUTHORITY SECTION:
.                       10705   IN      NS      j.root-servers.net.
.                       10705   IN      NS      h.root-servers.net.
.                       10705   IN      NS      k.root-servers.net.
.                       10705   IN      NS      m.root-servers.net.
.                       10705   IN      NS      b.root-servers.net.
.                       10705   IN      NS      g.root-servers.net.
.                       10705   IN      NS      e.root-servers.net.
.                       10705   IN      NS      c.root-servers.net.
.                       10705   IN      NS      a.root-servers.net.
.                       10705   IN      NS      l.root-servers.net.
.                       10705   IN      NS      d.root-servers.net.
.                       10705   IN      NS      i.root-servers.net.
.                       10705   IN      NS      f.root-servers.net.
;; Query time: 110 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Jun 09 19:09:21 NZST 2014
;; MSG SIZE  rcvd: 271
 
But it is now working!
 I deleted the contents of resolv.conf then restarted bind9. Not sure if this fixed the problem.

---

