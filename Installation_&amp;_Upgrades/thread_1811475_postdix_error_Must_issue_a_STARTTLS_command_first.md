---
title: "postdix error: Must issue a STARTTLS command first"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by cwhite13 on 2011-07-24
I've been working on this for a couple of months. I seemed to have exhausted Google and other Ubuntu wikis leading to a whole new level of frustration. .I'm running Ubuntu 10.10 server. I've installed a postfix-mysql-dovecot mail server. Everything seems to be running fine internally. If I try to relay smtp to smtp.gmail.com, it doesn't go. I have he following errors in my /var/log/mail.log: Jul 24 16:59:26 losalamos postfix/qmgr[10015]: 6E9752E0620: removed
Jul 24 16:59:29 losalamos postfix/smtp[11863]: DCA6F2E063F: to=<newsmax@reply.newsmax.com>, relay=smtp.gmail.com[74.125.157.109]:587, delay=2.6, delays=0.04/0/1.9/0.63, dsn=5.7.0, status=bounced (host smtp.gmail.com[74.125.157.109] said: 530 5.7.0 Must issue a STARTTLS command first. f4sm3791303yhn.69 (in reply to MAIL FROM command))
Jul 24 16:59:30 losalamos postfix/qmgr[10015]: DCA6F2E063F: removed

This result has been consistent for at least a couple of months. Any additional assistance would be great. I keeping thinking it's something simple I've overlooked.

Thanks - Clay

---

### Post by cwhite13 on 2011-07-28
I found another tutorial, 
[[FONT=Calibri][SIZE=3][COLOR=#800080]http://souptonuts.sourceforge.net/postfix_tutorial.html[/COLOR][/SIZE][/FONT]]("http://souptonuts.sourceforge.net/postfix_tutorial.html"), following this, I was able to check my entries and clean up my main.cf file. I reloaded postfix, tried agin. Got the same error, but got another error just befor the STARTTLS error. The error, "
[FONT=Calibri][SIZE=3]cannot load Certificate Authority data: disabling TLS support" indicates that something in the postfix sasl CA configuration. Planning to check, see if I can find where the Main.cfg thicks the Certs are.[/SIZE][/FONT]

---

