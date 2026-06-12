---
title: "Main Server extremely slow last few hours"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2009-08-12
Hi

Has anyone else seen this? Iam getting 10 KB/s speeds.

---

### Post by wayne_cat on 2009-08-12
no problems from germany ... about 150 KB/s via mobile broadband ... that's the maximum for my UMTS network

---

### Post by rajeev1204 on 2009-08-12
> **wayne_cat said:**
> no problems from germany ... about 150 KB/s via mobile broadband ... that's the maximum for my UMTS network

You using main server or german? Main server had 58 MB of updates.Anyways i got half of them installed till now.

---

### Post by wayne_cat on 2009-08-12
main

```
root@macbook:~# cat /etc/apt/sources.list |grep com |grep -v src
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb http://archive.canonical.com/ubuntu karmic partner
deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
root@macbook:~# 

```

---

### Post by dentaku65 on 2009-08-12
I can confirm that main servers are slow at the moment.
Italian servers are slow by default :-)

---

### Post by taavikko on 2009-08-12
```
Fetched 10.2MB in 20s (500kB/s)                                                                     
Reading package lists... Done

```

and that's as fast this slow thing can do...
Mainserver in use.

---

### Post by rajeev1204 on 2009-08-12
Hmm i think some route between my place and main is messed up.

---

### Post by wayne_cat on 2009-08-12
tested again ... here is a  little german lesson for free :)

```
Es wurden 19,0MB in 3min 6s geholt (102kB/s)                                   
Vorkonfiguration der Pakete ...
```

---

### Post by plun on 2009-08-12
> **rajeev1204 said:**
> Hmm i think some route between my place and main is messed up.

Ok also from Sweden against Main..."Fetched 4331kB in 5s (793kB/s)"

You have **Network Tools** within Meny System > Administration

Run **Traceroute**  >  archive.ubuntu.com

---

### Post by Kareeser on 2009-08-12
Could be throttled somewhere in between. Can you switch to a local server and try again? That fixed the problem for me with the main Canadian server.

---

### Post by rajeev1204 on 2009-08-12
> **plun said:**
> Ok also from Sweden against Main..."Fetched 4331kB in 5s (793kB/s)"

You have **Network Tools** within Meny System > Administration

Run **Traceroute**  >  archive.ubuntu.com


Here it is

 (192.168.1.2)                             0.282ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              1.296ms 
 1:  192.168.1.1 (192.168.1.1)                              1.166ms 
 2:  192.168.1.1 (192.168.1.1)                              1.191ms pmtu 1464
 2:  ABTS-KK-dynamic-001.0.172.122.airtelbroadband.in (122.172.0.1)  44.771ms asymm  3 
 3:  ABTS-KK-Static-157.32.166.122.airtelbroadband.in (122.166.32.157)  46.875ms 
 4:  ABTS-KK-Static-009.32.166.122.airtelbroadband.in (122.166.32.9)  45.268ms 
 5:  122.175.255.29 (122.175.255.29)                       44.041ms 
 6:  125.21.167.25 (125.21.167.25)                         52.854ms asymm  8 
 7:  ldn-b2-link.telia.net (213.248.88.205)               208.392ms asymm  8 
 8:  ldn-tch-i2-link.telia.net (80.91.250.214)            208.609ms 
 9:  ldn-tch-i1-link.telia.net (80.91.250.217)            212.089ms 
10:  113069-ldn-tch-i1.c.telia.net (213.248.74.42)        318.784ms asymm 14 
11:  canonical-gw.datahop.net (195.72.130.230)            321.946ms asymm 14 


Dont know what to read of this.

---

### Post by rajeev1204 on 2009-08-12
Aah never mind, i switched to a singapore server and got the updates.

ia32 libs is the last update i got btw.Iam on 64 bit.

Somewhere the routing gone bad i think.

---

### Post by vishalrao on 2009-08-13
yes rajeev, there were the regular "submarine cable cuts" recent posts in other indian broadband/tech related forums especially affecting airtel :) though my bsnl connection wasnt affected it seems to me...

---

