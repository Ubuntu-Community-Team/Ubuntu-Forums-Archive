---
title: "Postfix not allowing remote smtp"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by xvampyricx on 2010-04-18
Not sure where to post this. But I fully have my server and everything up, MySQL, PHP5, Apache2, Postfix, Courier, SQMail, can't remember what else atm. 

I installed mailx and used the mail command to send an email to my external email address, worked just fine. sent it to another email, worked as well.

But the problem is, I do 'telnet localhost 25' to test it like they say, it connects. I run 'ehlo localhost' Nothing happens.

I've tried setting it up with Thunderbird on my home pc and it connects to the IMAP & POP servers just fine, but it cannot establish a connection with SMTP, I've tried changing the SMTP port to other ones, still no luck.

Oh BTW, I use Ubuntu 8.04 LTS (Hardy Heron)

---

### Post by xvampyricx on 2010-04-19
Bump. Really need this fixed.

---

