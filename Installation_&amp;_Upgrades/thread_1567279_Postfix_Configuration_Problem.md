---
title: "Postfix Configuration Problem"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by elcidsps on 2010-09-03
Greeting Gurus!

I have an issue that i am certain is not unique; however I have yet to find a solution.  I have set up a simple virtual postfix mail server with the following configuration:

```

#General Setup Parameters
smtpd_banner = $myhostname ESMTP $mail_name
biff = no
append_dot_mydomain = no
readme_directory = no
myhostname = lsintegrations.com
myorigin = lsintegrations.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
relayhost = mailstore1.secureserver.net
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
mydestination = 
virtual_uid_maps = static:5000 
virtual_gid_maps = static:5000

#Limit And Code Parameters
delay_warning_time = 4h 
unknown_local_recipient_reject_code = 450 
maximal_queue_lifetime = 7d 
minimal_backoff_time = 1000s 
maximal_backoff_time = 8000s 
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16 
smtpd_soft_error_limit = 3 
smtpd_hard_error_limit = 12

#Restriction Parameters
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit 
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit 
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_helo_required = yes 
smtpd_delay_reject = yes 
disable_vrfy_command = yes

#Virtual Maps And Lookup Parameters
alias_maps = hash:/etc/postfix/aliases 
alias_database = hash:/etc/postfix/aliases 
virtual_mailbox_base = /var/spool/mail/virtual 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf 
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

```and the following master configuration:
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
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
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
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
    -o smtp_fallback_relay=
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

```Problem is:

If I am on the mail server I can send mail to say...a gmail account using sendmail.  If I use a workstation with a mail client like Thunderbird, I can receive mail from a gmail account but I cannot send to an email account.  Error log follows:

```

Sep  3 13:52:34 mailserver imapd: LOGIN, user=spsimmons, ip=[::ffff:192.168.1.112], port=[56009], protocol=IMAP
Sep  3 13:52:34 mailserver postfix/smtpd[1007]: connect from unknown[192.168.1.112]
Sep  3 13:52:35 mailserver postfix/smtpd[1007]: NOQUEUE: reject: RCPT from unknown[192.168.1.112]: 554 5.7.1 <elcidsps@gmail.com>: Relay access denied; from=<spsimmons@lsintegrations.com> to=<elcidsps@gmail.com> proto=ESMTP helo=<[192.168.1.112]>
Sep  3 13:52:39 mailserver postfix/smtpd[1007]: disconnect from unknown[192.168.1.112]

```Anyone have any ideas?  Any help would greatly be appreciated.  Cheers!

---

### Post by elcidsps on 2010-09-03
Greeting Gurus!

I figured out what the problem was and will post it here in case someone else runs into it.

In the main.cf file:
```

mynetworks= 127.0.0.0/8,192.168.1.0/24

```Where 192.168.1.0 is my local network.  Cheers!

---

