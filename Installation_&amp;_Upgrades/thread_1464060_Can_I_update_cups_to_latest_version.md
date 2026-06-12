---
title: "Can I update cups to latest version?"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by dmbminaret on 2010-04-27
Hi,
Maybe a silly question. I have searched the forum and google without much success. 

Is there a way to upgrade cups to support the latest printers? For example if I am using 8.04 LTS server and I buy a newish printer, it won't work. Am I able to add a repository or apt-get upgrade to get the latest version?

Thanks.

---

### Post by zvacet on 2010-04-28
You can add repo to your source list and solved problem that way.Even better is to wait for few days and then upgrade Hardy to Lucid.It will be direct upgrade,because both are LTS.

---

### Post by dmbminaret on 2010-04-28
Thanks, but I can't find a repo to add anywhere. Are you able to advise what it is?

Thanks.

---

### Post by zvacet on 2010-04-29
I think it is better to upgrade then add repository from other version.With upgrade you will get two things in same time;new LTS version and new drivers.

---

### Post by dmbminaret on 2010-04-29
Thanks again zvacet, I do plan to however I forged through to get the printer working. For anyone else who reads this, I didn't actually get to update cups but installed the latest version of gutenprint which contained the drivers. This was also no simple task until I came across this site which has a .deb installer for it (and it seems the required dependencies).

[http://www.openprinting.org/driver/gutenprint/](http://www.openprinting.org/driver/gutenprint/)

Click the link for 5.2.5 (DEB for LSB 3.2)

Hope that helps someone.

---

### Post by zvacet on 2010-04-29
I´m glad you fix it.Sorry if I was not much of help.

---

