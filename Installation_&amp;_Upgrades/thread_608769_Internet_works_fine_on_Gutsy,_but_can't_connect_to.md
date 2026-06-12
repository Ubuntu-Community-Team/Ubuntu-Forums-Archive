---
title: "Internet works fine on Gutsy, but can't connect to belnet"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by Devoske on 2007-11-10
Hi,

I installed Ubuntu Gutsy a couple of days ago and everything works, except for the part when I try to download new stuff through a terminal. For example : 

Writing extended state information... Klaar
Err [http://ftp.belnet.be](http://ftp.belnet.be) gutsy/main linux-backports-modules-2.6.22-14-generic 2.6.22-14.10
  404 Not Found [IP: 193.190.198.20 80]
Err [http://ftp.belnet.be](http://ftp.belnet.be) gutsy/main linux-backports-modules-generic 2.6.22.14.21
  404 Not Found [IP: 193.190.198.20 80]
E: Failed to fetch [http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.22/linux-backports-modules-2.6.22-14-generic_2.6.22-14.10_i386.deb:](http://ftp.belnet.be/pub/mirror/ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.22/linux-backports-modules-2.6.22-14-generic_2.6.22-14.10_i386.deb:) 404 Not Found [IP: 193.190.198.20 80]

since I'm new to this, I really don't know what to do, but I need certain programs for my school... I have a DSL connection.

Thanks !

---

### Post by viciouslime on 2007-11-10
I think that site is just down... If you try accessing it through your browser you'll see you also get a 404. What is it you need exactly? Maybe someone will be able to give you an alternative location for it :)

---

### Post by viciouslime on 2007-11-10
Actually looking at it a bit more closely, I think you just have the wrong address, try this: [http://ftp.belnet.be/mirror/ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.22/]("http://ftp.belnet.be/mirror/ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.22/")
:)

---

### Post by Devoske on 2007-11-10
I solved it :p I was downloading everything like software sources from ftp.belnet.be. This was my standard server. Now I use the main server and everything works fine ! Thanks anyway :)

---

