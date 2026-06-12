---
title: "Setting up mail server on LAN"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by usmanma on 2010-08-12
I want to setup mail server on LAN (Local Area Network). How do I setup local SMTP server to be able to send emails? Please advice, Thanks.

---

### Post by lisati on 2010-08-12
You might want to look into [Postfix]("https://help.ubuntu.com/community/PostfixBasicSetupHowto").

---

### Post by odinfromvalhalla on 2010-08-12
apt-get install postfix

during conf is going to ask you if you want it to be an internet mail server or local, if i remember correctly.

---

### Post by usmanma on 2010-08-13
Thanks for your help :)

---

### Post by usmanma on 2010-08-13
> **odinfromvalhalla said:**
> apt-get install postfix

during conf is going to ask you if you want it to be an internet mail server or local, if i remember correctly.

Yeah, its ask that its "Internet Site" or "Local domain". I chose it to be "Internet site" as I want to be able to send emails to other domains.

Do you guys know, if we could use google's smtp server to send emails to internet domains?

---

