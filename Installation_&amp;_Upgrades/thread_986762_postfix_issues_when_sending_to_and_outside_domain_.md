---
title: "postfix issues when sending to and outside domain like gmail"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by genesimmons4201 on 2008-11-18
Here is a copy of my log I just wondered if you might know why I would be getting these errors

 match_hostname: LONDON14-1279657910.sdsl.bell.ca ~? 127.0.0.0/8
Nov 19 03:35:13 persephone postfix/smtpd[3934]: match_hostaddr: 76.70.7.182 ~? 127.0.0.0/8
Nov 19 03:35:13 persephone postfix/smtpd[3934]: match_hostname: LONDON14-1279657910.sdsl.bell.ca ~? 173.45.226.0/24
Nov 19 03:35:13 persephone postfix/smtpd[3934]: match_hostaddr: 76.70.7.182 ~? 173.45.226.0/24
Nov 19 03:35:13 persephone postfix/smtpd[3934]: match_list_match: LONDON14-1279657910.sdsl.bell.ca: no match
Nov 19 03:35:13 persephone postfix/smtpd[3934]: match_list_match: 76.70.7.182: no match
Nov 19 03:35:13 persephone postfix/smtpd[3934]: send attr request = disconnect
Nov 19 03:35:13 persephone postfix/smtpd[3934]: send attr ident = smtp:76.70.7.182


main.cf

myorigin = persephone.thoughtforge.ca
myhostname = persephone.thoughtforge.ca
biff = no
append_dot_mydomain = no
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
home_mailbox = Maildir/
#unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
mydomain = thoughtforge.ca
smtp_helo_timeout = 60s
smtpd_recipient_limit = 32
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject, reject_non_fqdn_hostname, reject_invalid_hostname, permit
#smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, check_policy_service inet:127.0.0.1:60000 permit permit_inet_interfaces
#smtpd_data_restrictions = reject_unauth_pipelining
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_sender_restrictions = permit_sasl_authenticated, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_helo_required = no
disable_vrfy_command = yes
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
mailbox_size_limit = 0
recipient_delimiter = +
delay_warning_time = 4h
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
local_recipient_maps =
mydomain = thoughtforge.ca
mydestination = persephone.thoughtforge.ca
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


tls_random_source = dev:/dev/urandom 

smtpd_sasl_security_options = 
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated check_relay_domains reject_unauth_destination reject
#smtpd_recipient_restrictions = reject_unauth_pipelining permit_mynetworks permit_sasl_authenticated reject_non_fqdn_recipient reject_unknown_recipient_domain permit_inet_interfaces reject_unauth_destination
broken_sasl_auth_clients = yes

---

