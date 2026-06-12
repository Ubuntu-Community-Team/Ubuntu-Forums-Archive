---
title: "Home network inter-family mail server"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by petersfreeman on 2012-06-13
**Background**

We now live in an area where our link to the internet is an expensive wireless connection using the cellular system.

Members of our family emails each other a lot, with large attachments such as videos, pictures, etc. 

**Goal**

I want to set-up a LAN mail server that we can use for family members where the mail just stays within the LAN and does not go out onto the Internet.

**Progress**

I installed Ubuntu 12.04 LTS Server 64 bit on a spare machine following the guide at this web site:

[INDENT][The Perfect Server - Ubuntu 12.04 LTS (Apache2, BIND, Dovecot, ISPConfig 3)]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3")[/INDENT]

**Results**

The domain I am using is made up (e.g. arbutusgrove.net) and I suspect that I also need to have the server act as its own DNS

**Questions**

[LIST=1]
[*]What do I need to do to get this working?
[*]Can you recommend links to further advice on this topic?
[/LIST]

Thank you,

Peter

---

### Post by petersfreeman on 2012-06-13
I went out and registered my domain name, so that should eliminate one problem.

---

### Post by petersfreeman on 2012-06-19
The problem was simple.  Everything was working fine.  In Thunderbird, I just needed to specify the server by ipaddress and the userid as **user@domain** instead of just **user**

---

