---
title: "Working MTA after installation?"
date: 2018-06-14
forum: Installation &amp; Upgrades
---

### Post by pksings2 on 2018-06-14
I'm struggling to find a workable MTA solution. Postfix works until spamassasin, amavis and dovecot are attempted to be coordinated with it. By itself it's a spammers dream. Courier installs but doesn't accept mail from outside, as does Citadel, sendmail is way beyond my limits of patience to install and configure. And Zimbra does not have an install candidate for 18.04 yet.

Any suggestions anyone?  It should work after being installed. Preferably with some kind of spam filtering, blacklisting and will deliver internal and external mail.  So far the only one that actually works after install is Postfix. But getting it to do the other stuff is more than I can stomach anymore.

---

### Post by TheFu on 2018-06-14
I use postfix as an email gateway and Zimbra as the enterprise communications server.   The gateway is 1 VM and Zimbra is the other.  I wouldn't run both the gateway and end-user stuff on the same system.

Learning to configure all this stuff takes time. There isn't any point-n-click solution that I'm aware.

---

