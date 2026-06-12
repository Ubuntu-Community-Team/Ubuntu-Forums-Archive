---
title: "Help needed to configure Ssmtp"
date: 2012-07-27
forum: Installation &amp; Upgrades
---

### Post by bentech4u on 2012-07-27
HI Friends

i installed and configured Ssmtp and successfully getting mails on my gmail ID

but i need to keep one copy of root mail in the local /var/mail/root also..now i am not getting root mails in local

my configuration is

```
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=mygmail@gmail.com
# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=smtp.gmail.com:587
# Where will the mail seem to come from?
rewriteDomain=gmail.com

AuthUser=mygmail@gmail.com
AuthPass=gmail_password
UseTLS=YES
UseSTARTTLS=YES

hostname=mygmail@gmail.com

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES
FromLineOverride=YES

```


```
# sSMTP aliases
#
# Format:       local_account:outgoing_address:mailhub
#
# Example: root:your_login@your.domain:mailhub.your.domain[:port]
# where [:port] is an optional port number that defaults to 25.

root:mygmail@gmail.com:smtp.gmail.com:587

```

---

