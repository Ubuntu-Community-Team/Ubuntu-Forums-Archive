---
title: "Beware Server Distro Upgrade"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by kj6zd on 2011-10-19
Hi all, I performed a distribution upgrade from 11.04 to 11.10 of a 32bit Server installation. This computer was hosting an E-Mail Server, POSTFIX and DOVECOT. It was setup with a few virtual users and running perfectly fine before upgrade. Apparently, the distro upgrade also plug's in a newer version of Dovecot and possibly a number of other things, not known to me yet.
Unfortunately, :shock: my entire e-mail system (don't know why, my FTP server too) stopped working. Authentication is fixed beyond repair! So far I found a major difference between my screwed up e-mail server and the upgraded =D>install. They use completely different configuration file structure and as in my case don't bother to leave it alone during upgrade. At the same time they'll fix the the new installation beyond repair ](*,). All my configuration backup files must have asked for deletion since they are not present anymore. 
I am not a LINUX geek and usually need assistance from someone that has written some configuration examples. With the new release, I can't find any of them either anymore at least not relating to the 11.10 release. 

I chose Ubuntu over the others because I thought it was the easiest from all Linux flavors. In the past this was true until this 11.10 release. It really hosed my system and caused a lot of work, research and other unnecessary destruction. If I want this kind of experience, I can run Windows. 
My point is, I can't learn every six month a new file structure, check every and all configuration file and modify them appropriately or learn how differently things are handled! Too Old for that!!!![-X[-X

P.S. This is NOT the first release upgrade I performed, but the first that hosed the system.

---

