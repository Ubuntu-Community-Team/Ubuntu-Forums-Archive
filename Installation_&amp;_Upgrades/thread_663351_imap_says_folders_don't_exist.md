---
title: "imap says folders don't exist?"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by firestorm_v1 on 2008-01-10
Greetings All:  

Time for fun with IMAP! ok, well not that fun.

Here's what's going on.  I'm using dapper (ubuntu 6.06) and have installed the courier-IMAP mail server.  In conjunction with that I have also installed Squirrelmail for web-based email service.

The issue is that if a user is authenticated and logs in, they get an error from SM stating "ERROR: IMAP server dropped connection".   After checking the /var/log/mail.log I get this:

Jan  9 21:01:16 inhouse imaplogin: Connection, ip=[::ffff:127.0.0.1]
Jan  9 21:01:16 inhouse imaplogin: chdir Maildir: No such file or directory

I have tried that with an existing user on the system and a user that I created post-install and the results are the same.

Any suggestions?

---

