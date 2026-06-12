---
title: "install dns server"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by mostafamm on 2012-06-08
hello

i know a little english.

how install dns server in ubuntu server 12.04 . in environment command

thank you

---

### Post by dino99 on 2012-06-08
into a terminal (ctrl+t) run:


 gksu gedit /etc/resolv.conf

and add:

nameserver 8.8.8.8 
(this is an example to get "google" server)

then save this file

---

### Post by SeijiSensei on 2012-06-08
I think the OP wants to install a DNS server, not configure one as a resolver.

The standard DNS server software is bind9 from the Internet Software Consortium.  It's pretty demanding to configure, but I'd start with [this document](https://help.ubuntu.com/12.04/serverguide/dns.html).  You're probably interested in the configuration for a "[primary master]("https://help.ubuntu.com/12.04/serverguide/dns-configuration.html#dns-primarymaster-configuration")."

---

