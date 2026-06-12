---
title: "Asterisk on 9.10 - use package or build from source? How to get config?"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by adante on 2010-03-07
Can someone explain to me the status of the asterisk package in 9.10? Is it supposed to work out of the box?

I am trying to install it but I cannot figure out how to get some base configuration files that comes with the asterisk package. Assuming there is one. How can I find out? If not, where can I get some reference configuration files that will work with 9.10?

I have tried purging asterisk, reinstalling, dpkg-reconfigure asterisk, and my /etc/asterisk directory remains empty. (Hilariously 'dpkg-reconfigure asterisk' complains if there is no /etc/asterisk directory -- but doesn't do anything with it if there is)

Now I've taken a look at some of the asterisk on ubuntu guides around and they mainly involve building from source.

Why is this? Is the 9.10 asterisk package broken? 

I had a nice asterisk 1.6 setup working on 8.10 but it no longer works in 9.10. I assume this is because of changes in the configuration. So I want a base configuration which I know works and which I can then bring my own configuration into.

---

