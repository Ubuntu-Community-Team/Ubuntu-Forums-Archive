---
title: "Installing squirrelmail"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by qwerty2 on 2007-02-01
Hi everyone

I have used apt-get and installed squirrelmail, I got the invalid command php_flag, googled and found I need to install libapache2 as apache2 wouldnt restart. After installing libapache it restarted fine.

If I go to [www.domain.com/squirrelmail/](www.domain.com/squirrelmail/) I get page not found, what have I missed?

Will it show squirrelmail to domains ALREADY on the server or will it add it to new ones only?

I havent changed anything in "squirrelmail-configure" what do I need to set there, please help, thanks in advance.

---

### Post by Nik_Doof on 2007-02-01
depends really on how you've got your apache2 configured. Check /etc/apache2/sites-enabled/ and see if theres a squirrelmail entry, I cant check the contents of the deb as i'm at work at the moment.

---

### Post by qwerty2 on 2007-02-01
Hi Andrew

Thanks for the reply, I sent you a PM

---

