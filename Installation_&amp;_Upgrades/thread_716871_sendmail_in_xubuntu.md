---
title: "sendmail in xubuntu"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by Diana Rogger on 2008-03-06
Hi,

Can someone help me how to install and configure sendmail ?

I want the webserver to send a test email.

How can I do this?

I install webmin but webmin is telling me that the sendmail is not installed or configured.

Thanks

---

### Post by prshah on 2008-03-06
sudo apt-get install sendmail

then

sudo gedit /etc/mail/sendmail.mc

then

sudo /etc/init.d/sendmail restart

Cheers,
PRShah

---

### Post by Diana Rogger on 2008-03-06
Hi PRShah,

It ia working.

Thanks.

Regards

---

