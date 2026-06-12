---
title: "broadband modem stops after mail server configuration"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by 10ghost on 2010-08-27
Hi all,
I just configured my system to be a mail server after following this howto 
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Normally before the configuration i use a huawei E1550 to browse on it but now it no longer works.
It connects to the internet but refuses to browse.
I cannot open any webapge or site for now.
I suspect it has to do with the shorewall configuration i must have changed that has caused this.
Any ideas on how i can resolve this or even what i can do to guide you better in solving this problem.
Thanks for your anticipated cooperation

---

### Post by 10ghost on 2010-08-28
I believe it is the interface file that has a problem.
I added this to it now
ppp0 detect dhcp,

But it still does not work.
Any suggestions?

---

