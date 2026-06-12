---
title: "Diskless Ubuntu?"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by new2linux09 on 2012-03-10
I am looking into (no tests done yet) the concept of using the Diskless Ubuntu set up instead of Thin Clients as we have several P4's that I'd like to take advantage of. Is it possible to set up a Diskless boot client and server without having the server act as the DHCP server? We already have a DHCP server implemented and and controlling multiple segmented networks. 

I read through the set up outlined here: 
[https://help.ubuntu.com/community/DisklessUbuntuHowto#Setup_your_client]("https://help.ubuntu.com/community/DisklessUbuntuHowto#Setup_your_client")
yet it seems this is very dependent on the DHCP server being tied with the boot server.

I should add the current DHCP uses mac association so every machine gets the same IP every time.

---

### Post by vikjon0 on 2012-03-11
Yes it is possible. It is called proxyDHCP and you can use dnsmasq.

---

