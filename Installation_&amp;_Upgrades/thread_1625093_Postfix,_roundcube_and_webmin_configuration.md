---
title: "Postfix, roundcube and webmin configuration"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by lostinwoods on 2010-11-18
Hi 
I have installed Ubuntu 10.10 server on vmware and want to install roundcube mail server on that so that I can host my email server.

I have installed webmin and can access the server via port 10000

but don;t have any clue what to do next.
as far as I can understand I need to do following things in line:

1) Change my hostname to actual domain i want emails to come and send thrugh like mail.demomailserver.com
2) install postfix and configure that
3) change my MX recods from hosting server to point to my own IP
4) as my IP is via ADSL so i need to use some sort of DHCP or BIND?? service
5) Install roundcube software and create mailboxes

do i need LDAP as well?
please correct me if I have got this right!!

---

### Post by jsra on 2010-11-18
Hi,

maybe u should try to look in this thread [http://ubuntuforums.org/showthread.php?t=185913&highlight=flurdy](http://ubuntuforums.org/showthread.php?t=185913&highlight=flurdy)
The guide that flurdy has there is very comprehensive and it also includes Roundcube. Going through that could help you.

---

### Post by lisati on 2010-11-18
It might be easier if you tend to one thing at a time. What I did on my server was to install Apache and Postfix first, and get them running. Then I installed webmin. It was some months before I installed things like squirrelmail and roundcube.

---

### Post by lostinwoods on 2010-11-18
thank you jsra

i have already tried that but somehow lack the terminal command capabilities due to high exposure of MS GUI (:oops:)

what i have done is installed a fresh Ubuntu 10.10 server and run tasksel and installed mail server and lamp.

can u suggest what to do next  like install what packages and in which order.

thank you in advance
> **jsra said:**
> Hi,

maybe u should try to look in this thread [http://ubuntuforums.org/showthread.php?t=185913&highlight=flurdy](http://ubuntuforums.org/showthread.php?t=185913&highlight=flurdy)
The guide that flurdy has there is very comprehensive and it also includes Roundcube. Going through that could help you.

---

### Post by lostinwoods on 2010-11-18
thank u lisati

what i needed is a step by guide
i have installed mail server and pamp via tasksel command

tell me where to go from here and how to configure it.

thank u in advance

> **lisati said:**
> It might be easier if you tend to one thing at a time. What I did on my server was to install Apache and Postfix first, and get them running. Then I installed webmin. It was some months before I installed things like squirrelmail and roundcube.

---

