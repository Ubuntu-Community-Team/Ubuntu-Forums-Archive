---
title: "Mutt and fetch email"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by badnack on 2011-12-07
Hi at all, i'm setting up mutt to handle my gmail account.
I can already retrieve and send email (using fetchmail and msmtp respectively); but i've an annoying issue yet: i can't use the G command to check email into mutt.
I've tried to configure pop_host and others variables, but when mutt tries to check email gives me a connection error, like it can't connect to the google's servers due to wrong address.
I've checked and i've used the correct pop address, even because the same address works correctly with fetchmail.
I've thought that could be due to ssl, but i didn't found how solve.
Suggestions :)?

---

### Post by internetprofiles1 on 2011-12-09
check the port settings and verify ssl or ttl, I do not know what else it could be.

---

### Post by andrew.46 on 2011-12-13
Have you had a quick look at this guide:

[Howto] Use Mutt with Gmail
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

Might make life a bit easier for you?

---

### Post by badnack on 2011-12-21
thanks at all for the support, i've finally setted the G button using imap protocol instead of pop3 ;)

---

