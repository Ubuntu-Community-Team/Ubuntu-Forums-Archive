---
title: "postfix installation"
date: 2016-05-09
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2016-05-09
somewhere I made a wrong turn, ...


grep -v ^# main.cf



```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no


readme_directory = /usr/share/doc/postfix

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = ronald-desktop
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = home.xxxx.biz, ronald-desktop, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
html_directory = /usr/share/doc/postfix/html
```

echo "This is the body of the email" | mail -s "This is the subject line" [email]ronald@xxxx.com[/email]

gives me in the logfile:
> May 10 11:48:32 ronald-desktop postfix/pickup[10406]: 9F8751C224A: uid=1000 from=<ronald>
May 10 11:48:32 ronald-desktop postfix/cleanup[10463]: 9F8751C224A: message-id=<20160510034832.9F8751C224A@ronald-desktop>
May 10 11:48:32 ronald-desktop postfix/qmgr[10407]: 9F8751C224A: from=<ronald@ronald+desktop@elmit.biz>, size=496, nrcpt=1 (queue active)
May 10 11:48:33 ronald-desktop postfix/smtp[10465]: 9F8751C224A: to=<ronald@elmit.com>, relay=ASPMX.L.GOOGLE.com[2404:6800:4008:c01::1b]:25, delay=0.59, delays=0/0/0.44/0.15, dsn=5.1.2, status=bounced (host ASPMX.L.GOOGLE.com[2404:6800:4008:c01::1b] said: 553-5.1.2 The sender address <ronald@ronald+desktop@xxxx.biz> is not a valid 553 5.1.2 RFC-5321 address. iu8si160359pac.78 - gsmtp (in reply to MAIL FROM command))
May 10 11:48:33 ronald-desktop postfix/cleanup[10463]: 608CF1C224B: message-id=<20160510034833.608CF1C224B@ronald-desktop>
May 10 11:48:33 ronald-desktop postfix/bounce[10466]: 9F8751C224A: sender non-delivery notification: 608CF1C224B
May 10 11:48:33 ronald-desktop postfix/qmgr[10407]: 608CF1C224B: from=<>, size=2617, nrcpt=1 (queue active)
May 10 11:48:33 ronald-desktop postfix/qmgr[10407]: 9F8751C224A: removed
May 10 11:48:33 ronald-desktop postfix/error[10478]: 608CF1C224B: to=<ronald@ronald+desktop@xxxx.biz>, relay=none, delay=0.01, delays=0/0/0/0, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to home.xxxx.biz[60.xxx.143.133]:25: No route to host)

Where have I introduced my host name into the from line?

---

