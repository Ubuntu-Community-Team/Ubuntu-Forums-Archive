---
title: "ipopd not listening ?"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by optimaco on 2006-07-22
Hi,

I'm trying to configure Ubuntu 5.10 server as an intranet mail server.
I have managed to install postfix properly as mails can be sent to the server via smtp without errors.
I want the users on the intranet to be able to retrieve their mail via pop3 / pop3s.
I did this type of configuration on Debian Sarge before, and all that was needed was to apt-get install ipopd.
However, when I do this on Ubuntu 5.10, then netstat -at, it seems that no server is listening on the pop3 or pop3s ports :( .
Am I missing something ? How do I start the pop3 server / make it available for intranet clients?

---

### Post by optimaco on 2006-07-23
Hmm, answering my own posts...
OK, the problem (with my Debian Sarge background) is that the inetd superserver is not installed by default in Ubuntu Server. ](*,) 
As ipop3d relies on this server for external requests, of course it could not work...
Simply installing the superserver (apt-get install inetd) solves the problem!

---

