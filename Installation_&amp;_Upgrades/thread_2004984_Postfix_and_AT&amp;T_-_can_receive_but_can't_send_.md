---
title: "Postfix and AT&amp;T - can receive but can't send email"
date: 2012-06-16
forum: Installation &amp; Upgrades
---

### Post by CaptianNemo on 2012-06-16
Hello, I am trying to use postfix on AT&T but without much luck.
I am able to receive email but I am not able to send emails, when I try to send an email i get an email with the following in it. ```
host 98.139.221.42[98.139.221.42] said: 530     authentication required - for help go to     [http://help.yahoo.com/sbc/dsl/mail/pop/pop-11.html](http://help.yahoo.com/sbc/dsl/mail/pop/pop-11.html) (in reply to MAIL FROM     command)
```Here is my postconf -n
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
masquerade_domains = nautiluscraft.com
mydestination = /etc/postfix/local-host-names
mydomain = nautiluscraft.com
myhostname = nautiluscraft.com
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 98.139.221.42:587
smtp_sasl_password_maps = hash:/etc/postfix/smtp_sasl_password_map
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks reject_unauth_destination
smtpd_sasl_local_domain =
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
virtual_maps = hash:/etc/postfix/virtusertable
```Here is my main.cf
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = nautiluscraft.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = /etc/postfix/local-host-names
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain = 
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
#smtp_sasl_auth_enable = yes
#smtp_sasl_password_maps = hash:/etc/postfix/password
#smtp_sasl_security_options = noanonymous
virtual_maps = hash:/etc/postfix/virtusertable
relayhost = 98.139.221.42:587
masquerade_domains = nautiluscraft.com
mydomain = nautiluscraft.com
smtp_use_tls = yes
#smtpd_sasl_auth_enable = yes
#smtp_sasl_mechanism_filter = plain,login
#smtpd_sasl_type = dovecot
#smtpd_sasl_path = private/auth
smtp_sasl_password_maps = hash:/etc/postfix/smtp_sasl_password_map
inet_interfaces = all

```Here is my master.cf
```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
#submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       n       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


```I have been trying to get this to work for days.
I have google'ed everything I can think of, and nothing I have found has worked.
Any help would be greatly appreciated.

---

### Post by efflandt on 2012-06-17
You need to set it up so you authenticate to the AT&T relay with your AT&T username (ie, full e-mail address) and password.  So you need to configure **sasl_passwd** for postfix.  But it has been many years since I played around with that, so I don't know if that automatically updates sasl_passwd.db.  When I last did that SBC/Yahoo mail relays required SMTP_AUTH, but were still using port 25.

You might include lines in sasl_passwd for outbound.att.net and any name(s) that resolves to and names that the IP addresses resolve to.

Also what is port 587?  Current AT&T mail client instructions say to use port 465 and have SSL enabled, so I would think you would use that port for relaying postfix.

---

### Post by CaptianNemo on 2012-06-18
> **efflandt said:**
> You need to set it up so you authenticate to the AT&T relay with your AT&T username (ie, full e-mail address) and password.  So you need to configure **sasl_passwd** for postfix.  But it has been many years since I played around with that, so I don't know if that automatically updates sasl_passwd.db.  When I last did that SBC/Yahoo mail relays required SMTP_AUTH, but were still using port 25.

You might include lines in sasl_passwd for outbound.att.net and any name(s) that resolves to and names that the IP addresses resolve to.

Okay, I tried that, no luck.

> **efflandt said:**
> Also what is port 587?  Current AT&T mail client instructions say to use port 465 and have SSL enabled, so I would think you would use that port for relaying postfix.

I was under the impression that port 587 was the correct port to use as postfix no longer uses port 465. I did change it though, I got this instead: ```
[SIZE=2]lost connection with smtp.att.yahoo.com[98.138.31.74] while receiving the initial server greeting[/SIZE]
```

---

