---
title: "Need 8.10 updates"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by Rgibbons on 2011-05-26
The regular repositories have moved. Anyone know where I can find repository updates for 8.10?

---

### Post by novinick on 2011-05-26
[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) try here , for educational and archived purposes

---

### Post by mörgæs on 2011-05-26
Don't use an obsolete release of Ubuntu. It is a major security threat.

Best is a live boot of one of the supported releases and after that a fresh install.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by novinick on 2011-05-27
yeah right also is threat breathing radioactive air ???

so let's talk about security shall we ?

ubuntu has not had for a LONG time until 8.04 firewall on default download .iso
end even then has to use **ufw** or **gufw** explicitly to be enabled

also new editions has desktop sharing enabled per default which 
is sloter for cable internet population , enywone can connect to your box
(about 60% us home has cable broadband)
that means if you are on cable broadband , theres a chance your a toast

and everybody wants adobe FLASH
what is bigger threat then this ?
way of spreading mallware is nulifying needs for clasic firewaals which becomes inefective


also plenty or all critical files in /etc/ are readable by ordinary user

also from rebooting is quite easy to change all passes
if you have direct acces to box (recovery mode log you as root)

the list may be continued by cloud services ,for any os
which are inherenly insecure by nature

there is no way too to stop leaking of user information
on windows there are specialised firewals that STOPS privacy leaks or at least try as bes thay can,
not default firewall.
this is on allunixes.

has anyone take a look at app/armor or SElinux ? looks nice
and some other security measure ,policykit ?

---

