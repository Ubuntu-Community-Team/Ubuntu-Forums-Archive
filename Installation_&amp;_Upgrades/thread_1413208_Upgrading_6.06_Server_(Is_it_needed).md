---
title: "Upgrading 6.06 Server (Is it needed?)"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by breit on 2010-02-22
Hi, 
I'm just curious weather it can be done and is it worth it?
 
I currently have a 6.06 LAMP Server running as a small Webserver (Intranet) and Content Filter / Firewall (Dansguardian and Squid).
 
If there is already a post on this subject can someone point me in the right direction my search strings didn't bring up any results.
 
Thanks

---

### Post by OrangeCrate on 2010-02-22
It's totally up to you whether you want to do something now. The server edition will continue to receive maintenance updates through June of 2011.

Personally, I don't run a server, so I can't comment on an upgrade. I'm sure that someone will be along to comment on that portion of your question...

[https://lists.ubuntu.com/archives/ubuntu-announce/2009-July/000123.html](https://lists.ubuntu.com/archives/ubuntu-announce/2009-July/000123.html)

---

### Post by slakkie on 2010-02-22
Needed? No, 6.06 is supported till June 2011 ([https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)).

I would do the upgrade before that time, although it is possible after as well (see link in sig).

If you need a newer version of $application that is not available on Dapper or its dependencies cannot be met on Dapper I would do an upgrade. But since you didn't give any indication that you are in such a situation, there is no clear need to upgrade.

Hope this helps.

---

### Post by Dragonbite on 2010-02-22
No sense updating until 10.04 LTS is released at least.

Since 6.06 is supported for a little while longer, you will have the luxury of waiting a couple of months for Lynx to work through any issues that arise, test it and get it set up before 6.06 is dropped.

I have 8.04 LTS right now, and I'm going to wait for 10.04 to come out.  I would probably not even do that except I now regret adding a desktop environment and GUI so upgrading to 10.04 will allow me to remove that and update my settings from what I've learned since.

Otherwise, unless you need to update something like PHP, Dansguardian, MySQL, etc. or find yourself tweaking the hell out of the system you should be good for a while.

Running a virtualized server would make things pretty easy; you could make a new VM of the new server, turn off the old server and test it out for a while. If it doesn't work, you shut off the new one and turn on the old one.  Plus you could split out the content fitler and the LAMP server and update them individually.

---

