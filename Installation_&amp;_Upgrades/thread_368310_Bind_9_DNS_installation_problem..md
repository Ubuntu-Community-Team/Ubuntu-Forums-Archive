---
title: "Bind 9 DNS installation problem."
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by rpr on 2007-02-23
Hi,

I am trying to replace windows 2003 DNS server with a BIND9 DNS on ubuntu

This is my /etc/bind/named.conf:
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "kvkov.be" {
        type master;
        file "/etc/bind/zones/kvkov.be.db";
};
// 10.101.x.x
zone "101.10.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.101.1.in-addr.arpa";
};

```

My /etc/bind/zones/kvkov.be.db:
```

kvkov.be.       IN      SOA     testserver.kvkov.be.    admin.kvkov.be. (
// Do not modify the following lines!
                                2006081401
                                28800
                                3600
                                604800
                                38400
)
kvkov.be.       IN      NS      testserver.kvkov.be

testserver      IN      A       10.101.1.8

```

This is my /etc/bind/zonesrev.101.10.in-addr.arpa:
```

@ IN SOA testserver.kvkov.be. admin.kvkov.be. (
                        2006081401;
                        28800;
                        604800;
                        604800;
                        86400
)

                     IN    NS     testserver.kvkov.be.
1                    IN    PTR    kvkov.be

```


When I test (dig kvkov.be) the settings with both dns I got this:
BIND DNS:
```
; <<>> DiG 9.3.2 <<>> kvkov.be
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 14818
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;kvkov.be.                      IN      A

;; Query time: 0 msec
;; SERVER: 10.101.1.8#53(10.101.1.8)
;; WHEN: Fri Feb 23 09:30:41 2007
;; MSG SIZE  rcvd: 26
```


With MS DNS:
```
; <<>> DiG 9.3.2 <<>> kvkov.be
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21014
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;kvkov.be.                      IN      A

;; ANSWER SECTION:
kvkov.be.               600     IN      A       10.101.1.2
kvkov.be.               600     IN      A       10.101.1.4
kvkov.be.               600     IN      A       10.101.1.1

;; Query time: 19 msec
;; SERVER: 10.101.1.1#53(10.101.1.1)
;; WHEN: Fri Feb 23 09:31:32 2007
;; MSG SIZE  rcvd: 74
```


I hope anyone can help me out. To fix bind to give answer and make the reply the same.
Thanks in advance.

---

### Post by Strider on 2007-02-23
For one thing, in your /etc/bind/zones/kvkov.be.db file you need to make sure a ";" appears after each of the settings in the SOA record, similar to how you have it in the reverse zone file.

Bind9 comes with a zone check utility that will verify your config and point out errors.  
1) named-checkconf
2) named-checkzone

Maybe the forward zone file is not loading up.  You're also restarting the service after the changes, correct?

-Mike

---

