---
title: "weird ip adress"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by leocoppens on 2012-05-02
Hello all,

I have installed ub.serv.11.10 and installed lamp server (at least I clicked on it during installation). Did install it on a virtual box soft and installed correctly besides for the ip address that I get now which is weird. when I run ifconfig I get 10.0.2.15 as inet addr when I was expecting something like 192.168.0.106.

I did install it twice today and the same frustrating result. I did install it a few months ago and got an expected 192.168.0.106 ip which i could connect to with filezilla and zencart but this weird one doesnt work.

Maybe lamp isn't there? maybe something is missing?

can somebody pls help this newby?

Thanks a lot girls and guys

---

### Post by darkod on 2012-05-02
Since you are working in VB that is a virtual adapter and it gets the 10.0.2.15 IP by default.

In the Settings in VB for that machine, click on Network, then on Adapter #2 tab, and enable the adapter selecting Host-only option. That would create a second adapter inside your machine (eth1).

Set it up with what ever IP you want. You will probably want a static IP for a server.

---

### Post by leocoppens on 2012-05-03
Thank you mate! That's what I was missing! It is working now!
I apreciate it! ;)

---

