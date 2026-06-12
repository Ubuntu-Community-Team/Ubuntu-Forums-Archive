---
title: "dumb terminal network login"
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by kenworth on 2005-06-06
I'm a newbie with Ubuntu now almost running perfectly on Dell laptop (just a couple of screen issues to resolve).

I wish to be able to login from my W98 PC via our LAN. I currently have an old RH6.0 server that I can access from any of the windows PCs on the network using Telnet or TeraTerm. When I try to connect to the Dell, I get the message ;
Telnet: Unable to connect to remote host: Connection refused

I have added my PCs to /etc/hosts and /etc/hosts.allow just in case there was some security issue involved. I didn't have to do this with RH, it was happy to receive telnet from any machine.

Any suggestions would be gratefully received    O:)

---

### Post by Tomy on 2005-06-07
[QUOTE=kenworth]I'm a newbie with Ubuntu now almost running perfectly on Dell laptop (just a couple of screen issues to resolve).

I wish to be able to login from my W98 PC via our LAN. I currently have an old RH6.0 server that I can access from any of the windows PCs on the network using Telnet or TeraTerm. When I try to connect to the Dell, I get the message ;
Telnet: Unable to connect to remote host: Connection refused

I have added my PCs to /etc/hosts and /etc/hosts.allow just in case there was some security issue involved. I didn't have to do this with RH, it was happy to receive telnet from any machine.

Any suggestions would be gratefully received    O:)[/QUOTE]

Perhaps you do not have the telnet server installed on the Dell?
Try:
$ sudo apt-get install telnetd

Another possibility is that you are not using the correct local ip address. From the Dell try this command:
$ ifconfig
You should see the Dell's ip address in the eth0 section.

Hope this helps
Tomy

---

### Post by kenworth on 2005-06-07
That worked a treat!, Thanks for your prompt assistance.

---

