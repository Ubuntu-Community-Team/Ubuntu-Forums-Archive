---
title: "Ubuntu on Bladecenter HS20 and SAN"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by loafimus on 2006-10-10
I was just wondering if anyone has gotten Ubuntu Server installed on a Blade and booting off a SAN.

We just got our Bladecenter here at work and was really hoping to use Ubuntu as our webserver.  We need to have it boot off of a SAN using a Qlogic card.

Has anyone configured one of these this way?  If so let me know, if not I'll try to post steps here as to how I get it working... if I do =)

---

### Post by elicriffield on 2006-10-23
I had it working under dapper, It worked out of the box with a HS20 bladecenter and SAN boot. I just tried upgrading to edgy and am having problems with the qlogic drivers, Theres a bug open to fix this though. 

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/67463](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/67463)

But in production i'd go with dapper for the long term support anyway, you just have to roll your own xen.

Eli

---

