---
title: "Trying to install sendmail"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by bhepple on 2007-01-16
I'm trying to install sendmail with my own /etc/mail/sendmail.mc file.

When I cd /etc/mail and do `make' I get this error:

make: *** No rule to make target `/usr/share/sendmail-cf/m4/cf.m4', needed by `/etc/mail/databases'. 

dpkg -S /usr/share/sendmail/cf/m4/cf.m4 gives:
sendmail-cf: /usr/share/sendmail/cf/m4/cf.m4

... sendmail-cf is installed.

If I create a symbolic link to resolve /usr/share/sendmail-cf/m4/cf.m4 then I get a little further but it ends with:

Warning: .cf file is out of date: sendmail 8.13.8 supports version 10, .cf file is version 0
No local mailer defined
QueueDirectory (Q) option must be set


Strange - it all `just works' on my other systems.

Any ideas?


Thanks


Bob


PS I'm on edgy eft

---

### Post by dcstar on 2007-01-16
> **bhepple said:**
> I'm trying to install sendmail with my own /etc/mail/sendmail.mc file.
.......
PS I'm on edgy eft

Personally I would try installing the **postfix** package, it is sendmail compatible and seems to work straight away.

---

### Post by bhepple on 2007-01-17
... so is sendmail on ubuntu so hopelessly broken?


Cheers


Bob

---

### Post by psylvester on 2007-03-23
unfortunately I wanted to know "how to install sendmail",  this forum is awesome..
-- Where ever I see people asking "how to install sendmail" - people reply with everything but sendmail.

SENDMAIL WILL EVER WORK WITH UBUNTU? Any Idea? - A correct reply is much appreicated.

The replies i have seen so far,
30% - I dont remember (most crap reply)
20% -I have installed using apt-get install sendmail (which didnt work)
50%- giving other options (which is better).

Please if someone know how to install "sendmail" pls do reply.

Thanks,
Sylvester

---

