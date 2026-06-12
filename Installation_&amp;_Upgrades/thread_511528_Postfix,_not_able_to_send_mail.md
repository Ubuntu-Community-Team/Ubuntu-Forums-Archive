---
title: "Postfix, not able to send mail"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by edeiten on 2007-07-27
I have a LAMP web server running on the latest Ubuntu version, behind a dynamic IP address. It is working great. I installed Postfix and friends with no problems. But now I am unable to send email. I am attempting to send mail from my server to a 3rd part, known good mail server and it times out. My settings and the log entry is below. The only thing I have attempted to change is 'mynetworks'. What does this need to be set to? what is the number after the slash (i.e. 127.0.0.0/??) Thanks, 

LOGS:
Jul 27 20:56:26 postfix/pickup[8873]: 744138001C5: uid=0 from=<root>
Jul 27 20:56:26  postfix/cleanup[9049]: 744138001C5: message-id=<20070728015626.744138001C5@<server name>
Jul 27 20:56:26 postfix/qmgr[8874]: 744138001C5: from=<root@mail......>, size=627, nrcpt=1 (queue active)
Jul 27 20:56:26 postfix/qmgr[8874]: 744138001C5: to=<erich@......>, relay=none, delay=0.05, delays=0.04/0.01/0/0, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to .....: Connection timed out)

SETTINGS:
#myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
#delay_warning_time = 4h
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
debug_peer_list = 127.0.0.0
debug_peer_level = 2
myhostname = <server name>
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.......org, <servername>, localhost.localdomain, localhost
relayhost =
#mynetworks = 127.0.0.0/8
mynetworks_style = host
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

---

