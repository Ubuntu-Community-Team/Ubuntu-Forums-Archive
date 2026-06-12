---
title: "SMTP mail loop?"
date: 2015-07-06
forum: Installation &amp; Upgrades
---

### Post by jonnier on 2015-07-06
I am building myself a new mail sever using OpenSMTP, Dovecot, Clam and SpamAssassin(with spampd), if I just have a normal mail delivery direct to the mailbox, everything works fine, but when I try and implement routing through Clam and then SpamAssassin, I seem to get a loop.

Attached is my smtpd file, I start two instances of clamsmtpd to have AV scanning in and out, but it does the same with just scanning in as well.

I have also attached the mail.log which seems to show mail bouncing around.  Any one have any ideas of where I'm going wrong?

---

