---
title: "apt-get Connection Failed, Timed Out"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by joecm on 2006-08-23
Noobie here... be gentle

I installed Ubuntu Server Version (LAMP edition) this morning and the install was as easy as advertised.  It was up and running in minutes.

However, I have spent hours today trying to get the apt-get functionality to work.  Each time that I run it, it works for a little bit and then hangs (connection failed, connection timed out) midway through a file.  However, after stalling for a minute, it cancels the hung file and and the next file downloads successfully.  

I have read countless entries online, mostly suggesting that this is somehow a firewall or proxy issue.  It seems to me if I can get some of the files, it isn't the proxy or firewall.

I have tried to change the sources_list file to point to archive. instead of us.archive and security.archive.  It seemed to work a bit better, but not enough to work successfully.  Are the servers just overloaded?  Is this typical or a one day thing?

Anybody know what is going on?

---

### Post by K.Mandla on 2006-08-23
It's possible. I get the same timeouts a lot, especially during the day. Overall, the U.S. servers seem problematic, to be honest. 

You could try doing your updates at an off time, like 3 a.m. ... or maybe that's extreme. ;)

You could also try changing anything in your sources.list that starts with "us." to "uk." or even "de." Midday in the U.S. is late evening in Europe, so it works out to everyone's benefit.

I've also heard that the servers in Belgium (be.) are quite responsive.

---

