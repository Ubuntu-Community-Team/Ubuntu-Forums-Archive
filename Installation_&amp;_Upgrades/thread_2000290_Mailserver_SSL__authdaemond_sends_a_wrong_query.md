---
title: "Mailserver SSL | authdaemond sends a wrong query?"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by SeaKing on 2012-06-09
Hey,

currently I'm trying to setup an emailserver using this tutorial: [http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/](http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/)

Now I tried to login with test-admin account (email: [EMAIL="admin@domain.tdl"]admin@domain.tdl[/EMAIL] PW: changeme) but get the following errors:
```

syslog:
Jun  9 13:18:50 h2026662 authdaemond: received auth request, service=imap, authtype=login
Jun  9 13:18:50 h2026662 authdaemond: authmysql: trying this module
Jun  9 13:18:55 h2026662 authdaemond: SQL query: SELECT email, password, "", 5000, 5000, "/var/spool/mail/virtual", CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/'), quota, name, "" FROM user WHERE email = 'admin'
Jun  9 13:18:50 h2026662 authdaemond: zero rows returned
Jun  9 13:18:50 h2026662 authdaemond: no password available to compare
Jun  9 13:18:50 h2026662 authdaemond: authmysql: REJECT - try next module
Jun  9 13:18:50 h2026662 authdaemond: FAIL, all modules rejected
Jun  9 13:18:50 h2026662 imapd-ssl: LOGIN FAILED, method=PLAIN, ip=[::ffff:77.64.173.118]
Jun  9 13:18:55 h2026662 authdaemond: received auth request, service=imap, authtype=login
Jun  9 13:18:55 h2026662 authdaemond: authmysql: trying this module
Jun  9 13:18:55 h2026662 authdaemond: SQL query: SELECT email, password, "", 5000, 5000, "/var/spool/mail/virtual", CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/'), quota, name, "" FROM user WHERE email = 'admin'
Jun  9 13:18:55 h2026662 authdaemond: SQL query: SELECT email, password, "", 5000, 5000, "/var/spoo$
Jun  9 13:18:55 h2026662 authdaemond: zero rows returned
Jun  9 13:18:55 h2026662 authdaemond: no password available to compare
Jun  9 13:18:55 h2026662 authdaemond: authmysql: REJECT - try next module
Jun  9 13:18:55 h2026662 authdaemond: FAIL, all modules rejected
Jun  9 13:18:55 h2026662 imapd-ssl: LOGIN FAILED, user=admin, ip=[::ffff:77.64.173.118]


```and mail.log tells the same.

I told thunderbird to use:

mail.domain.tdl as the smtp and imap Server
SSL on Port 993
Password/plain

The error message I that irritates me most is:

```
Jun  9 13:18:55 h2026662 authdaemond: SQL query: SELECT email, password, "", 5000, 5000, "/var/spool/mail/virtual", CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/'), quota, name, "" FROM user WHERE email = 'admin'

```If this is really the query which is sent so the mysql server the result will always be empty!

Where did I or the tutorial went wrong?

```

#/etc/courier/authdaemonrc

authmodulelist="authmysql"
authmodulelistorig="authuserdb authpam authpgsql authldap authmysql authcustom authpipe"
daemons=5
authdaemonvar=/var/run/courier/authdaemon
DEBUG_LOGIN=2
DEFAULTOPTIONS=""
LOGGEROPTS=""

#--------------------------------------------------------------------------------------------------

#etc/courier/authmysqlrc

MYSQL_SERVER localhost
MYSQL_USERNAME mail
MYSQL_PASSWORD password
MYSQL_PORT 0
MYSQL_DATABASE mail
MYSQL_USER_TABLE user
MYSQL_CRYPT_PWFIELD password
MYSQL_UID_FIELD 5000
MYSQL_GID_FIELD 5000
MYSQL_LOGIN_FIELD email
MYSQL_HOME_FIELD "/var/spool/mail/virtual"
MYSQL_MAILDIR_FIELD CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/')
MYSQL_NAME_FIELD name
MYSQL_QUOTA_FIELD quota

```the subdomain mail.mydomain.com is registered and I also put it on the MX Record
I also tried to send an email from an other provider to my mailserver and got this:

```

Jun  9 13:02:51 h2026662 postfix/smtpd[10026]: connect from mout.web.de[212.227.17.11]
Jun  9 13:02:51 h2026662 postfix/smtpd[10026]: NOQUEUE: reject: RCPT from mout.web.de[212.227.17.11]: 554 5.7.1 <user@web.de>: Sender address rejected: Access denied; from=<user@web.de> to=<admin@mydomain.tdl> proto=ESMTP helo=<mout.web.de>
Jun  9 13:02:51 h2026662 postfix/smtpd[10026]: disconnect from mout.web.de[212.227.17.11]


```

---

