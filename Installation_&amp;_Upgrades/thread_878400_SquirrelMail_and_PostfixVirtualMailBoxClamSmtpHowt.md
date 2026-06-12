---
title: "SquirrelMail and PostfixVirtualMailBoxClamSmtpHowto"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by SitUbuSit on 2008-08-02
I followed this guide:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

then this guide:

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

Skipping the ClamAV part for now.

Now I want to get webmail setup, so I followed this guide:

[https://help.ubuntu.com/community/Squirrelmail](https://help.ubuntu.com/community/Squirrelmail)

Eventually, I figured out that I had to add this to my dovecot.conf:

ssl_cert_file = /etc/ssl/certs/smtpd.crt
ssl_key_file = /etc/ssl/private/smtpd.key

Now, when I log-in with SquirrelMail, I get the message:

ERROR: Connection dropped by IMAP server.
Query: CAPABILITY

And in my mail.log, I see:

Aug  3 04:41:33 servername postfix/virtual[28514]: 426278520C: to=<someone@somewhere.com>, relay=virtual, delay=8791, delays=8791/0.02/0/0.06, dsn=4.2.0, status=deferred (maildir delivery failed: create maildir file /home/vmail/somewhere.com/someone/tmp/1217738493.P28514.servername: Permission denied)

Any ideas how to fix this?

---

### Post by SitUbuSit on 2008-08-03
Ok, I figured it out.  For the sake of anyone else who gets stuck on this:  The adddovecotuser script creates the domain name folders as root:root, and the folders under that as vmail:vmail, so I just has to run a chown in the vmail folder on all the directories there.

cd /home/vmail
sudo chown vmail:vmail *

Maybe that adddovecotuser script should be:
# Create the needed Maildir directories
/usr/bin/maildirmake.dovecot /home/vmail/$domain 5000:5000
/usr/bin/maildirmake.dovecot /home/vmail/$domain/$user 5000:5000

---

