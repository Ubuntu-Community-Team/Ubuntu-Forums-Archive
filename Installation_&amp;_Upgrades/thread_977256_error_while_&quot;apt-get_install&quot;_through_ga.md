---
title: "error while &quot;apt-get install&quot; through gateway"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by abirami6033 on 2008-11-10
I have installed ubuntu 8.04 server. The PC is behind the gateway protected with firewall, blocking all the downloads. I am new to linux and would like to get information about the configurations used by apt.

To configure the NAT in the gateway, for allowing the upgrade and installations through apt in my ubuntu server What are the urls and the port numbers that has tobe configured in the NAT of the gateway. 

The PC bypasses the proxy machine and the pc is configured with a static IP currently. 

When I looked into the /etc/apt/sources.list and I have the following urls are available
[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)

Can these urls be configured in NAT. Is there any specific port used by apt.

---

### Post by Mark224 on 2008-11-10
http uses port 80.  You can set up some firewall rules to allow these sites.

Normally port 80 is open so that you can use web browsers.

---

