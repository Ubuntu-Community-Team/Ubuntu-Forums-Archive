---
title: "Choose South African update site for local traffic"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by xibur on 2008-08-05
Hi,
I am from South Africa and would like to know where I should point my Ubuntu updater to ensure that local (South African) ADSL traffic is used when updating. This way I would not be using my international cap when updating Ubuntu. Local South African traffic is only charged after 10Gb whereas I have a 1Gb international traffic cap.

Currently my update sites point to variants of 
[http://za.archive.ubuntu.com](http://za.archive.ubuntu.com)....
but when I receive my usage report from Telkom all traffic is listed as international.

Is Adept Updater possibly using another route? Or is it simply a Telkom billing problem? 
I have contacted Telkom ADSL technical support and will update any feedback they have.

Any pointers/ideas?

Ruben

PS I did a traceroute to ensure no hops go outside South Africa:
traceroute to za.archive.ubuntu.com (155.232.191.229), 30 hops max, 40 byte packets
 1  10.0.0.2 (10.0.0.2)  3.750 ms  5.555 ms  6.742 ms
 2  * * *
 3  rrba-ip-lir-1-gig-0-0-0.telkom-ipnet.co.za (196.43.8.198)  394.003 ms  394.102 ms  394.187 ms
 4  196.43.25.138 (196.43.25.138)  394.269 ms  394.386 ms  395.062 ms
 5  internet-solutions-gw.telkom-ipnet.co.za (196.25.127.182)  395.154 ms  395.359 ms  395.451 ms
 6  cp3-rba-gi0-2.ip.isnet.net (168.209.86.165)  397.372 ms  325.008 ms  400.319 ms
 7  ch11-rba-gi0-1.ip.isnet.net (196.26.0.30)  400.370 ms  401.845 ms  411.770 ms
 8  mail.amorphous.net (168.209.115.218)  413.275 ms  414.354 ms  415.342 ms
 9  unknown.uni.net.za (155.232.191.229)  416.484 ms  417.391 ms  419.775 ms

---

### Post by zvacet on 2008-08-05
Adept>manage repositories there should be option to select server.Manual way is 

```
kdesu kate /etc/apt/sources.list
```

and replace existing code (**za** in your case) with your country code.Save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by xibur on 2008-08-21
Thanks for the reply!
All my sites (except security updates) are .za which would mean it should be local traffic when I am updating. But unluckily my bandwidth is still deducted from international traffic. 

When I have time I'll take it up with Telkom (the ISP) but unluckily it is quite a mission to get a response from them.

---

