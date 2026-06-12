---
title: "postfix on ubuntu- not working"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by lmcin on 2008-05-18
hi. just installed postfix on my ubuntu box. when i set the email program it came with to localhost, it says theres a LOAD ERROR when it sends/receives and has a bunch of numbers and then says something like 'directory or file not found'.

When i set the smtp servr to the name of the computer, it says "connected refused".

any ideas why? i used the default installation settings.

many tahnks

---

### Post by cdtech on 2008-05-18
> When i set the smtp servr to the name of the computer, it says "connected refused"

Firewall?

You need to allow smtp port 25 access. Try to > telnet localhost 25

---

### Post by lmcin on 2008-05-18
> **cdtech said:**
> Firewall?

You need to allow smtp port 25 access. Try to > telnet localhost 25

Yeh was thinking that but didnt think i had any firewall. I would have though localhost as the smtp server would have had the same effect as my computer name?

Well... I installed pfsense and SQUID. Would any of these block port 25 by default?

Sorry, this is for an assignment and i have to set up a whole heap of services. 

Also one quick question please- i installed pfsense but have no ieda to tell if it is working. How would I go about showing that it works? Can I block say port 80 to show that it dosnt work?

Many thanks

---

### Post by cdtech on 2008-05-19
I really don't know those firewall's personaly. I use Shorewall myself.

I would disable those and use the default iptables to be sure your port is working correctly first.

You have to add a rule to iptables, to open the port:
iptables -A INPUT -p tcp --dport 25 -j ACCEPT

Use "nmap localhost" to see if the port is open or not.

---

### Post by mitchell1234 on 2008-06-21
guys i need someone to help me configure squid! can someone post a squid.conf file? When I configured it ad try to run it on firefox its giving me access denied! This is something surely that has to do with the conf file mentioned above!

---

