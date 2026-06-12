---
title: "ettercap ubuntu server 10.04 Server! HELP ME!!"
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by clauss1 on 2014-07-20
[IMG]http://i60.tinypic.com/2d9oiev.png[/IMG]

PUTTY screen on UBUNTU 10.04 x86 server


Hey all! 


I put in / root Ettercap 0.8.0 and I'm interested in why I see the following error? 


root @ vps: ~ / # Ettercap Ettercap-0.8.0-G 


Ettercap NG-0.7.4_git copyright 2001-2011 Alor & Nagai 




Failed to initialize GTK +. Is X running? 


I understand that you can not install on ubuntu server? 


And if you know how to solve this problem please help me or tell me a program like Ettercap! thanks

And if you run the command Ettercap-T-q-M arp-i eth0-P dns_spoof / / I appears:

root@vps:~/ettercap-0.8.0# ettercap -T -q -M arp -i eth0 -P dns_spoof //


ettercap NG-0.7.4_git copyright 2001-2011 ALoR & NaGA


Listening on eth0...
ERROR : 19, No such device
[ec_capture.c:capture_init:146]


 pcap_open: SIOCGIFHWADDR: No such device

---

### Post by clauss1 on 2014-07-20
Upppp!

---

### Post by bapoumba on 2014-07-20
Closed for Staff review.

---

### Post by coffeecat on 2014-07-20
After staff discussion, the thread will remain closed.

Ettercap is for man in the middle attacks. Such things are not supported here.

---

