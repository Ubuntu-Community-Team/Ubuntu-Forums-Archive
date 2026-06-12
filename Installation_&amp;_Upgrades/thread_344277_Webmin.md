---
title: "Webmin"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by shdawson on 2007-01-22
Hi,


Put Ubuntu Server on my machine.  So far, love it.  Want to put Webmin on there, cannot find it as a package:
# apt-get install Webmin

returns no package found.


[https://help.ubuntu.com/community/WebminWithoutARootAccount?highlight=%28webmin%29](https://help.ubuntu.com/community/WebminWithoutARootAccount?highlight=%28webmin%29)

[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

So, do I need to get the webmin_1.320_all.deb to CD and install from there?


Thanks...

---

### Post by Nik_Doof on 2007-01-22
I dont think theres a package but you can install it quite easily by hand

Check out [this guide]("http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html#more-34")

---

### Post by shdawson on 2007-01-22
Thanks.

I would rather stay with apt-get if possible.  A buddy says Webmin is available on the Debian mirrors and to install netinstall through apt-get, then add data sources.  tried that, netinstall not available.  Do you know if netinstall is an option here?

If not, will go with the link you sent when I get back home.  Thanks again for the help here.

---

### Post by shdawson on 2007-02-01
OK, guess I am going to have to install it.

[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

Question, how do I access the root password for Ubutntu?  I am not clear on how to change it.


Thanks . . .

---

### Post by mpieters on 2007-07-26
You can always type:

$>sudo passwd root

and give root a password.  Then you have one.

---

### Post by flamacue on 2007-09-11
The [instructions]("http://www.webmin.com/deb.html") are on the [webmin website]("http://www.webmin.com").

Look for the section called "Using the Webmin APT repository".

:)

---

### Post by flamacue on 2007-09-11
Regarding changing the PW, see the 2nd question from their [FAQ]("http://www.webmin.com/faq.html"):

> How do I change my Webmin password if I can't login?

Included with the Webmin distribution is a program called changepass.pl to solve erecisely this problem. Assuming you have installed Webmin in /usr/libexec/webmin, you could change the password of the [COLOR="Red"]root[/COLOR] user to foo by running
```
/usr/[COLOR="Red"]share[/COLOR]/webmin/changepass.pl /etc/webmin [COLOR="Red"]root[/COLOR] foo
```

The parts in red are different from what's on their FAQ, specific to Ubuntu (Feisty, IME).  The command may require sudo, I don't recall.  It won't change the root password on your machine--just for your webmin login.  Once you're logged into webmin, you can sync the users with your accounts on the machine if you want...

---

