---
title: "Postfix &amp; Dovecot Virtual Mailbox MySql - Can't connect mailbox from Thunderbird"
date: 2021-12-02
forum: Installation &amp; Upgrades
---

### Post by kristy1024 on 2021-12-02
Hi:
I've got a VPS running Ubuntu 20.04.3 LTS.
I have **postfix **3.4.13 and **dovecot **2.3.7.2  installed.
I tested and everything was fine.
Next I reconfigured to use** virtual mailboxes** and **MySql**

I've got an email: [EMAIL="mailadm@softlinksys.com"]mailadm@softlinksys.com[/EMAIL]
I've got an MX record for **softlinksys.com** (at namecheap.com) pointing at **mail.softlinksys.com.**
You can MX Lookup and see that the MX for softlinksys.com points to mail.softlinksys.com.
The IP address that shows up is the IP of my VPS.

[COLOR=#b22222]**In both the postfix and dovecot configurations I'm confused as to where to put softlinksys.com and/or mail.softlinksys.com**[/COLOR]
My server is hosting more than 1 domain so email must work for **multiple domains** **-> multiple email addresses**.

I've got a MySql database: mailserver
I've got tables: virtual_domains, virtual_users, virtual_aliases
The domain softlinksys.com is in virtual_domains. I also tried mail.softlinksys.com.
The email [EMAIL="mailadm@softlinksys.com"]mailadm@softlinksys.com[/EMAIL] is in virtual_users with domain_id as the corresponding id in the virtual_domains table.

I don't think dovecot is having any trouble connecting to or reading the database. 
When I try to log into the [EMAIL="mailadm@softlinksys.com"]mailadm@softlinksys.com[/EMAIL] mailbox from Thunderbird (on a remote desktop) it says:
***Login to server mail.softlinksys.com with username [EMAIL="mailadm@softlinksys.com"]mailadm@softlinksys.com[/EMAIL] failed*** and gives me an opportunity to change the password.
The Account Name in Thunderbird is: [EMAIL="mailadm@softlinksys.com"]mailadm@softlinksys.com[/EMAIL]
The Email in Thunderbird is: [EMAIL="mailadm@softlinksys.com"]mailadm@softlinksys.com[/EMAIL]
The password is correct (I copied & pasted it directly from the database record).

/etc/dovecot/dovecot.conf
```
#################################################################
!include_try /usr/share/dovecot/protocols.d/*.protocol
dict {
  
}
!include_try local.conf
protocols = imap pop3 lmtp
##################################################################
```

/etc/dovecot/dovecot-sql.conf.ext
```
################################################
driver = mysql
connect = host=127.0.0.1 dbname=mailserver user=<********> password=<********> ##The user and password tested and connect to MySql correctly.
default_pass_scheme = SHA512-CRYPT
password_query = SELECT email as user, password FROM virtual_users WHERE email='%u';  ##Fields email and password are in the virtual_users table. The record is consistent with the values in Thunderbird.
################################################
```

/etc/dovecot/10-master.conf
```
################################################################
service imap-login {
  inet_listener imap {
    port = 143  ##This was set to 0 and that didn't work either.
  }
  inet_listener imaps {
    port = 993  ##These were remmed and that didn't work either.
    ssl = yes
  }
}
service pop3-login {
  inet_listener pop3 {
    port = 110  ##This was remmed and that didn't work either.
  }
  inet_listener pop3s {
    port = 995 ##These were remmed and that didn't work either.
    ssl = yes
  }
}
service submission-login {
  inet_listener submission {
    #port = 587
  }
}
service lmtp {
  unix_listener /var/spool/postfix/private/dovecot-lmtp {
    mode = 0600
    user = postfix
    group = postfix
  }
}
service imap {
 
}
service pop3 {
  
}
service submission {
  
}
service auth {
  unix_listener /var/spool/postfix/private/auth {
      mode = 0660
      user = postfix
      group = postfix
   }
   unix_listener auth-userdb {
     mode = 0600
     user = vmail
     #group =
  }
  user = dovecot
}
service auth-worker { 
  user = vmail
}
service dict { 
  unix_listener dict {
    
  }
}
################################################################
```

/etc/dovecot/10-auth.conf
```
######################################################################
disable_plaintext_auth = yes
auth_username_format = %n
auth_mechanisms = plain login
######################################################################
```

/etc/dovecot/10-ssl.conf
```
######################################################################
ssl = required
ssl_cert = </etc/letsencrypt/live/mail.softlinksys.com/fullchain.pem
ssl_key = </etc/letsencrypt/live/mail.softlinksys.com/privkey.pem
ssl_client_ca_dir = /etc/ssl/certs
ssl_dh = </usr/share/dovecot/dh.pem
ssl_prefer_server_ciphers = yes
ssl_min_protocol = TLSv1.2
######################################################################
```

I look at /var/log/syslog and I see this: ***softlinksys dovecot: imap-login: Disconnected (auth failed, . . .*** 
The rip and lip IP addresses in the error are both correct.
I look at /var/log/email.log and I see the same thing.

[COLOR=#b22222][B]Would dovecot throw a database error if it had trouble with the database connection or queries?
Why does the authorization fail and how can I troubleshoot it?[/B][/COLOR]

---

### Post by kristy1024 on 2021-12-02
On command line I tested the MySql connections:
postmap -q [EMAIL="mailadm@softlinksys.com"]mailadm@softlinksys.com[/EMAIL] mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
1
postmap -q softlinksys.com mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
1
postmap -q [EMAIL="spamme@softlinksys.com"]spamme@softlinksys.com[/EMAIL] mysql:/etc/postfix/mysql-virtual-alias-maps.cf
[EMAIL="test.alias@softlinksys.com"]mailadm@softlinksys.com[/EMAIL]

It looks like postmap is having no trouble connecting to the database.

Also, in /etc/dovecot/dovecot-sql.conf.ext
I remmed default_pass_scheme = SHA512-CRYPT
The passwords in the database are not encrypted.

[COLOR=#b22222]**I still cannot connect to the [email]mailadm@softlinksys.com[/email] mailbox from Thunderbird**[/COLOR]

---

### Post by kristy1024 on 2021-12-02
/etc/postfix/master.cf
```
smtp      inet  n       -       y       -       -       smtpd
submission inet n       -       y       -       -       smtpd
  -o syslog_name=postfix/submission
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_sasl_type=dovecot
  -o smtpd_sasl_path=private/auth
  -o smtpd_reject_unlisted_recipient=no
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       y       -       -       smtpd
  -o syslog_name=postfix/smtps
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_sasl_type=dovecot
  -o smtpd_sasl_path=private/auth
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING
pickup    unix  n       -       y       60      1       pickup
cleanup   unix  n       -       y       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
#qmgr     unix  n       -       n       300     1       oqmgr
tlsmgr    unix  -       -       y       1000?   1       tlsmgr
rewrite   unix  -       -       y       -       -       trivial-rewrite
bounce    unix  -       -       y       -       0       bounce
defer     unix  -       -       y       -       0       bounce
trace     unix  -       -       y       -       0       bounce
verify    unix  -       -       y       -       1       verify
flush     unix  n       -       y       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       y       -       -       smtp
relay     unix  -       -       y       -       -       smtp
        -o syslog_name=postfix/$service_name
showq     unix  n       -       y       -       -       showq
error     unix  -       -       y       -       -       error
retry     unix  -       -       y       -       -       error
discard   unix  -       -       y       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       y       -       -       lmtp
anvil     unix  -       -       y       -       1       anvil
scache    unix  -       -       y       -       1       scache
postlog   unix-dgram n  -       n       -       1       postlogd
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
```

/etc/postfix/main.cf
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
compatibility_level = 2
smtpd_tls_cert_file=/etc/letsencrypt/live/mail.softlinksys.com/fullchain.pem
smtpd_tls_key_file=/etc/letsencrypt/live/mail.softlinksys.com/privkey.pem
smtpd_use_tls=yes
smtpd_tls_auth_only = yes
smtpd_sasl_type = dovecot 
smtpd_sasl_path = private/auth 
smtpd_sasl_auth_enable = yes 
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks,reject_unauth_destination
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, defer_unauth_destination
smtpd_client_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_invalid_hostname, reject_unknown_client_hostname
smtpd_helo_restrictions = reject_unknown_helo_hostname
smtpd_sender_restrictions = reject_unknown_sender_domain, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_sender
mydestination = localhost
myhostname = softlinksys.com
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_transport = lmtp:unix:private/dovecot-lmtp
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf#, mysql:/etc/postfix/mysql-virtual-email2email.cf
smtputf8_enable = no
```

[COLOR=#b22222][B]I can't figure this out. I've gone through at least 4 tutorials. They all have slightly different settings.
I cannot make Thunderbird: [email]mailadm@softlinksys.com[/email] connect to its mailbox[/B][/COLOR] (NOTE: The password is correct. I pasted it directly from the database record - no encryption was used or set in the config (see above))

---

### Post by kristy1024 on 2021-12-02
I've made another edit to:
/etc/dovecot/dovecot-sql.conf.ext
```
default_pass_scheme = PLAIN
```

The password in the database is not encrypted.
I can change that later if I ever get this figured out.

If I set the mail server in Thunderbird to softlinksys.com instead of mail.softlinksys.com it will connect.
The MX record for softlinksys.com is mail.softlinksys.com SO
I still can't send emails from another account to [EMAIL="mailadm@softlinksys.com"]mailadm@softlinksys.com[/EMAIL]
I've tried setting the domain in virtual_domains to mail.softlinksys.com
When I do that and restart dovecot from the command line it hangs and won't return the cursor.
 
[COLOR=#b22222]**In dovecot virtual mailboxes MySql how can I correlate softlinksys.com (ie [EMAIL="mailadm@softlinksys.com"]mailadm@softlinksys.com[/EMAIL]) with the MX mail.softlinksys.com?**[/COLOR]

---

