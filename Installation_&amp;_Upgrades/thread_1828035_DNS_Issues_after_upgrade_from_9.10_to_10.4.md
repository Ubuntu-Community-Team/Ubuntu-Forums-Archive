---
title: "DNS Issues after upgrade from 9.10 to 10.4"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by isthisyournacho on 2011-08-18
I upgraded all our services from Ubuntu 9.10 to 10.4 and now the internal network keeps looking at our OLD email server to send mail.

I upgraded our email server a month ago, and after the upgrade was done mail was coming here fine.  Now after this upgrade it is looking at the old server, 10.1.1.95.  (the new is 10.1.1.96.)

Aug 18 12:23:12 SERVER postfix/smtp[32707]: 9023135A1A2: to=<EMAIL>, relay=mail.DOMAIN.com[10.1.1.95]:25, delay=0.28, delays=0.08/0.01/0.02/0.17, dsn=2.6.0, status=sent (250 2.6.0  <20110818162312.GA32693@ORIGINATING-SERVER> Queued mail for delivery)

I've checked /etc/resolv.conf and they are looking at our GoDaddy nameservers.  I have done an rdnc flush.

Also.. we have a local nameserver here but I only use that as a backup.  Here is my /etc/resolv.conf:

search DOMAIN.com
nameserver 216.69.185.14 (godaddy's nameserver)
nameserver 208.109.255.14 (godaddy's nameserver)
nameserver 10.1.1.121
nameserver 4.2.2.2

Thanks!

---

### Post by thefasterblueone on 2011-08-18
Try reducing the number of nameservers in your resolv.conf file. There is a limit of ( 3 ) maximum.

[http://www.cyberciti.biz/tips/linux-how-to-setup-as-dns-client.html]("http://www.cyberciti.biz/tips/linux-how-to-setup-as-dns-client.html")

---

### Post by isthisyournacho on 2011-08-18
Good catch!  I have done that and did /etc/init.d/networking restart but still get the same thing.

What's odd is that a dig from DOMAIN.com returns the server's public IP address which is what I expect.  dig to mail.DOMAIN.com returns an internal IP and its the incorrect one.  

;; ANSWER SECTION:
mail.DOMAIN.com.    3600    IN      A       10.1.1.95

;; AUTHORITY SECTION:
DOMAIN.com.         3600    IN      NS      ns27.domaincontrol.com.
DOMAIN.com.         3600    IN      NS      ns28.domaincontrol.com.

;; Query time: 7 msec
;; SERVER: 216.69.185.14#53(216.69.185.14)
;; WHEN: Thu Aug 18 15:56:26 2011
;; MSG SIZE  rcvd: 105

---

### Post by isthisyournacho on 2011-08-25
bump.

I thought I'd post more information that perhaps could help people resolve.  Here's my DOMAIN.com zone file:

```
$TTL 28800
DOMAIN.com.      IN      SOA     ns1.DOMAIN.com. syslog.DOMAIN.com. (
                                                        2010071301
                                                        28800
                                                        3600
                                                        604800
                                                        38400 )

DOMAIN.com.      IN      NS              ns1.DOMAIN.com.
;
;web servers
@               IN      A       10.1.1.210
web1            IN      A       10.1.1.210
web10           IN      A       10.1.1.20
web12           IN      A       10.1.1.21
web20           IN      A       10.1.1.125
web21           IN      A       10.1.1.131
;
;internals
internal1       IN      A       10.1.1.121
internal2       IN      A       10.1.1.122
;
;Database servers
mapdb2          IN      A       10.1.1.190
;
;backup servers
mapbak1         IN      A       10.1.1.252
;
;mail servers
mapexch         IN      A       10.1.1.96
;
;other
dev11           IN      A       10.2.1.20
l3map02         IN      A       10.1.1.123
;
;CNAMES
ns1             CNAME   internal1
ldap            CNAME   internal1
mail            CNAME   mapexch
backup          CNAME   mapbak1
www             CNAME   web1

DOMAIN.com. IN      MX      10      mail.DOMAIN.com.

```

Dig results inside of the network:

```
; <<>> DiG 9.7.0-P1 <<>> @4.2.2.2 mail.DOMAIN.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 34413
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.DOMAIN.com.           IN      A

;; ANSWER SECTION:
mail.DOMAIN.com.    3600    IN      A       10.1.1.95

;; Query time: 77 msec
;; SERVER: 4.2.2.2#53(4.2.2.2)
;; WHEN: Thu Aug 25 10:13:51 2011
;; MSG SIZE  rcvd: 53

```

Dig results outside of the network:

```
; <<>> DiG 9.7.0-P1 <<>> mail.DOMAIN.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18345
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;mail.DOMAIN.com.           IN      A

;; ANSWER SECTION:
mail.DOMAIN.com.    2067    IN      A       64.124.160.95

;; Query time: 10 msec
;; SERVER: 4.2.2.2#53(4.2.2.2)
;; WHEN: Thu Aug 25 10:13:46 2011
;; MSG SIZE  rcvd: 53

```

Note that the same server, 4.2.2.2, is responding with two different results.

---

### Post by isthisyournacho on 2011-08-25
Issue turned out to be an alias definition on the Cisco PIX firewall - not a Linux issue at all.  :\

---

