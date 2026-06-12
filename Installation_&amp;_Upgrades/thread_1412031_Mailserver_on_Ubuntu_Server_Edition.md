---
title: "Mailserver on Ubuntu Server Edition"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by brajzore on 2010-02-20
Hi everyone!

I have Ubuntu Server Edtiion on my server. During the installatino, I choosed to install the mailserver.

I have already configured the MTA.

I also configured the MDA(Dovecot). After I configured the MDA and tried to login on squirrelmail, plenty of MySQL error was generated. 

I deleted Dovecot and tried again to login on squirrelmail. Now, this message appears:

Error connecting to IMAP server: localhost.
111 : Connection refused

How can I resolve this? Resolve this on a simple way :-)

---

### Post by Bachstelze on 2010-02-20
Dovecot is not a MDA, it is an IMAP server, so obviously if you remove it, Squirrelmail won't be able to connect to it...

---

### Post by brajzore on 2010-02-20
> **Bachstelze said:**
> Dovecot is not a MDA, it is an IMAP server, so obviously if you remove it, Squirrelmail won't be able to connect to it...


But after I installed Dovecot, Squriellmail generated plenty of MySQL-errors.

---

### Post by brajzore on 2010-02-21
Someone who can tell me how I can solve this on a simply way?

---

