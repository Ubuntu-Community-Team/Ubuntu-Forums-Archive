---
title: "SPF and DKIM Not working [ mydomain.com  has no TXT record]"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by pradeep vallat on 2010-06-10
Hello,

I am new to Ubuntu and have installed Ubuntu 10.04 Server.

My Dns entry as follows :
mydomain.com.      IN      NS              ns1.mydomain.com.
mydomain.com.        IN      MX      10 mail.mydomain.com.
mydomain.com.        IN      TXT     "v=spf1 a mx mx:mail.myomain.com ip4:xxx.xxx.xx.x/24 all"


............................................
Post Fix main.cf
============================================================


spf-policyd_time_limit = 3600s
myorigin = mail.mydomain.com

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.mydomain.com 
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128, 121.243.0.0/24,
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,check_policy_service unix:private/policy-spf
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
virtual_alias_domain = mail.mydomain.com
virtual_alias_maps = hash:/etc/postfix/virtual


# DKIM
milter_default_action = accept
milter_protocol = 2
smtpd_milters = inet:localhost:8891
non_smtpd_milters = inet:localhost:8891

=====================================================================
I have added the following line in master.cf
======================================================================


policy-spf  unix  -       n       n       -       -       spawn
     user=nobody argv=/usr/sbin/postfix-policyd-spf-perl

=====================================================================

Test results :
host -t txt mydomain.com shows :

**mydomain.com has no TXT record**

Kindly help to fix it up

Thanks in advance.

---

