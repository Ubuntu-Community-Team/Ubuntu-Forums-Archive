---
title: "New server setup Sunday - considering UBUNTU"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by yorgo on 2010-02-19
Convinced my client to get rid of Win2003 SBS and go with a Linux or BSD variant. Hardware has been shipped. Poweredge 2970 and ready to be prepped. OS decision comes down to Ubuntu 9.10 or FreeBSD 8. I've been running FreeBSD on one of my own servers and it works like a champ but some Linux may be a better fit for this company.

Are there any "gotcha's" I should expect on a 2970? 

Is Postfix a good choice to replace Exchange 03? They know this will be limited to email only. 

Whats a good webmail package for Postfix?

Also how big a pain in the rear will Samba be when joining a Win 2008 domain? (they have an existing 08 server required for custom apps using MS SQL. 

Oh and yes, 1st post. sorry for dumping all these questions so soon. I'm a 15 year IT vet with Windows 2000/03/08, Netware, Linux (LAMP), and BSD. Worked plenty with Samba on AD but have not integrated with a 2008 server yet.

---

### Post by lisati on 2010-02-19
A basic LAMP installation is a good place to start on Ubuntu server edition. I'm running my website (apache2) and email server (postfix) without any major hassles, with the occasional tweak to help reduce incoming spam and misuse of my system.

---

### Post by Old_Grey_Wolf on 2010-02-19
Considering the server you are talking about, I wouldn't rule out the possibility that they may want to expand their cluster of computers, storage, or network. You may want to take a look at Ubuntu Enterprise Cloud at [http://www.ubuntu.com/cloud/private](http://www.ubuntu.com/cloud/private).

Ubuntu Enterprise Cloud supports virtualization; therefore, they can migrate to it over time rather than a "big bang" change.

---

### Post by tgalati4 on 2010-02-19
I'm running Hardy on an older poweredge 1750.  Hardy has wider support for commercial and open source packages.  It's easier to find pre-built packages for Hardy for many popular applications.

---

### Post by madverb on 2010-02-19
> **yorgo said:**
> Convinced my client to get rid of Win2003 SBS and go with a Linux or BSD variant. Hardware has been shipped. Poweredge 2970 and ready to be prepped. OS decision comes down to Ubuntu 9.10 or FreeBSD 8. I've been running FreeBSD on one of my own servers and it works like a champ but some Linux may be a better fit for this company.

Are there any "gotcha's" I should expect on a 2970? 

Is Postfix a good choice to replace Exchange 03? They know this will be limited to email only. 

Whats a good webmail package for Postfix?

Also how big a pain in the rear will Samba be when joining a Win 2008 domain? (they have an existing 08 server required for custom apps using MS SQL. 

Oh and yes, 1st post. sorry for dumping all these questions so soon. I'm a 15 year IT vet with Windows 2000/03/08, Netware, Linux (LAMP), and BSD. Worked plenty with Samba on AD but have not integrated with a 2008 server yet.

You've recommended something before researching it? I mean it's fantastic that you convinced them to go this way but I think this could end up being a bad experience for them.
There are options for very similar setups to Exchange like Zimbra.
You really need to look into it more.

---

### Post by pirateghost on 2010-02-20
> **madverb said:**
> You've recommended something before researching it? I mean it's fantastic that you convinced them to go this way but I think this could end up being a bad experience for them.
There are options for very similar setups to Exchange like Zimbra.
You really need to look into it more.


+1  

if you are going to be the primary support, you may find yourself in over your head if you cant deliver the goods...

---

