---
title: "SMTP does not work after automatic update"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by grr2 on 2014-03-06
Hello,

I use Ubuntu (12.04) as a Mail-Server and it worked very good for more than a year now.

Today I started the automatic update utility - it downloaded and installed the updates without error messages.

But now **sendmail/smtp does not work: I cannot connect to the mail-server** from a mail-client und nobody can send an e-mail to the server.

Details:

[LIST]
[*]sendmail version 8.14.4
[*]sendmail is running in the process list "sendmail: MTA: accepting connections"
[*]Pop(3) works
[*]"Telnet *ipaddress* 25" can not connect to the server.
[/LIST]

Any ideas or solutions?

Thank you,
GRR

---

### Post by TheFu on 2014-03-06
restore the sendmail.cf from a backup?  Tried that?

---

### Post by grr2 on 2014-03-07
You are right - thank you.

I've just found the problem - the updater added a new line to sendmail.cf, using new features. But the line was incorrect (an option for the daemon: the port and the address for listening has been added incorrect).

I changed the line and everything worked again.

Problem solved!

---

### Post by TheFu on 2014-03-07
Please mark thread as solved.

---

### Post by grr2 on 2014-03-07
Ok ;-)

---

