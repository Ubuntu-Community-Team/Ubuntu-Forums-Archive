---
title: "firewall controll for apt-upgrede"
date: 2022-12-23
forum: Installation &amp; Upgrades
---

### Post by naoqmon on 2022-12-23
Hello all,


I am new ubuntu user Japanese.
Sorry for my poor English.

I use ubuntu 22.04
When a firewall exists between Ubuntu sever and the Internet,
What addresses and ports i should set to open the firewall for apt-update or apt-upgrade?


Destination&#8594;&#65311;
service port&#8594;&#65311;


Thanks!

---

### Post by ian-weisser on 2022-12-23
Generally, you should not need to open anything unless you are blocking your own outgoing packets.

Apt will make an outgoing request (allowed), the server will respond to that request (allowed).

Outgoing requests use ordinary http.

---

### Post by naoqmon on 2022-12-25
Thank you for replying.

I was going to say that the firewall controls outbound packet.
I got http service is used as Apt, Thanks!
Destination is " [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) " right?

---

### Post by Impavidus on 2022-12-26
The urls can be found in /etc/apt/sources.list. I expect at least [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu), in addition to whatever local mirror you use. If you enabled additional sources, they can be found in the same file or in /etc/apt/sources.list.d/.

---

### Post by naoqmon on 2022-12-26
I got what I would like to know.
Thanks!

---

