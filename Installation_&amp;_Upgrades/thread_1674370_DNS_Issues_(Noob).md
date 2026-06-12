---
title: "DNS Issues (Noob)"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by MacBros on 2011-01-23
I installed ISPConfig, and got a domain through GoDaddy, and setup nameservers (ns1 and ns2) on that domain to my external IP. I also added A Records in ISPConfig for ns1 and ns2 to my external IP. I can't connect through my domain, but can through my external ip and I've waited 24 hours incase DNS had to update. Here's what I get with dig @localhost mydomain.com:

```

[root@server1 install]# dig @localhost macbrosgb.com
; <<>> DiG 9.3.6-P1-RedHat-9.3.6-4.P1.el5_5.3 <<>> @localhost macbrosgb.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 64688
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;macbrosgb.com.			IN	A

;; Query time: 2 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Jan 23 15:00:54 2011
;; MSG SIZE  rcvd: 31

[root@server1 install]#

```

Any help is really appreciated.

---

### Post by MacBros on 2011-01-23
Oh, and I'm using Bind9 on a CentOS 5.5 system.

---

