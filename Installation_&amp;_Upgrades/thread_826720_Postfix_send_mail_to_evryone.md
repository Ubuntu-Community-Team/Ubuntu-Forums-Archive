---
title: "Postfix send mail to evryone"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by death099 on 2008-06-12
hi, i'm trying to send mail but it only sends mail to certain people (xxxxx@uwc.ac.za) and it doesn't want to send mail to any other addresses such as gmail, hotmail etc, can anyone help?

here's my main.cf

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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

allow_untrusted_routing = yes

myhostname = csunx.uwc.ac.za
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = cs.uwc.ac.za, csunx.uwc.ac.za, localhost.uwc.ac.za, localhost, coe.uwc.ac.za
relayhost = itsnw.uwc.ac.za
mynetworks = 127.0.0.0/8 192.102.9.84
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_mechanism_filter = plain, login
smtpd_recipient_restrictions = permit_mynetworks
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

---

