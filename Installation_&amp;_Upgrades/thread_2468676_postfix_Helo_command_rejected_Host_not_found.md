---
title: "postfix Helo command rejected: Host not found"
date: 2021-11-07
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2021-11-07
An Australian Government site is trying to send me a (confirmation) email, but my mail server (set up and run by myself) rejects the incoming email.

---------
Nov 8 05:26:24 mail1 postfix/postscreen[1685596]: CONNECT from [103.151.87.18]:60820 to [xxx.xxx.xxx.xxx]:25
Nov 8 05:26:24 mail1 postfix/postscreen[1685596]: PASS OLD [103.151.87.18]:60820
Nov 8 05:26:28 mail1 postfix/smtpd[1685599]: connect from s2bulkseg.ato.gov.au[103.151.87.18]
Nov 8 05:26:31 mail1 postfix/smtpd[1685599]: NOQUEUE: reject: RCPT from s2bulkseg.ato.gov.au[103.151.87.18]: 450 4.7.1 <s2-smtp-ato-esa32.secureintellicentre.net.au>: Helo command rejected: Host not found; from=<nor...@mygovid.gov.au> to=<l...@xxx.com> proto=ESMTP helo=<s2-smtp-ato-esa32.secureintellicentre.net.au>
Nov 8 05:26:36 mail1 postfix/smtpd[1685599]: disconnect from s2bulkseg.ato.gov.au[103.151.87.18] ehlo=2 starttls=1 mail=1 rcpt=0/1 rset=1 quit=1 commands=6/7
---------
Appreciate if somebody could tell me if this may be due to something I've set up incorrectly.
All other mails to my domain come through

output from  postconf -n

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
compatibility_level = 2
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = 127.0.0.1, ::1, 122.252.221.29
inet_protocols = all
local_recipient_maps = $virtual_mailbox_maps
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
message_size_limit = 52428800
milter_default_action = accept
milter_mail_macros = i {mail_addr} {client_addr} {client_name} {auth_authen}
milter_protocol = 6
mua_client_restrictions = permit_mynetworks,permit_sasl_authenticated,reject
mua_relay_restrictions = reject_non_fqdn_recipient,reject_unknown_recipient_domain,permit_mynetworks,permit_sasl_authenticated,reject
mua_sender_restrictions = permit_mynetworks,reject_non_fqdn_sender,reject_sender_login_mismatch,permit_sasl_authenticated,reject
mydestination = $myhostname, localhost.$mydomain, localhost
mydomain = mydomain.com
myhostname = mail1.mydomain.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
non_smtpd_milters = inet:localhost:11332
postscreen_access_list = permit_mynetworks cidr:/etc/postfix/postscreen_access
postscreen_blacklist_action = drop
postscreen_dnsbl_action = drop
postscreen_dnsbl_sites = ix.dnsbl.manitu.net*2 zen.spamhaus.org*2
postscreen_dnsbl_threshold = 2
postscreen_greet_action = drop
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_dns_support_level = dnssec
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_tls_ciphers = high
smtp_tls_policy_maps = mysql:/etc/postfix/sql/tls-policy.cf
smtp_tls_protocols = !SSLv2, !SSLv3
smtp_tls_security_level = dane
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = mail1.mydomain.com
smtpd_client_restrictions = permit_mynetworks check_client_access hash:/etc/postfix/without_ptr reject_unknown_client_hostname
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks reject_invalid_helo_hostname reject_non_fqdn_helo_hostname reject_unknown_helo_hostname
smtpd_milters = inet:localhost:11332
smtpd_recipient_restrictions = check_recipient_access mysql:/etc/postfix/sql/recipient-access.cf
smtpd_relay_restrictions = reject_non_fqdn_recipient reject_unknown_recipient_domain permit_mynetworks reject_unauth_destination
smtpd_tls_cert_file = /etc/letsencrypt/live/mydomain.com-0001/fullchain.pem
smtpd_tls_ciphers = high
smtpd_tls_key_file = /etc/letsencrypt/live/mydomain.com-0001/privkey.pem
smtpd_tls_protocols = !SSLv2, !SSLv3
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_high_cipherlist = EDH+CAMELLIA:EDH+aRSA:EECDH+aRSA+AESGCM:EECDH+aRSA+SHA256:EECDH:+CAMELLIA128:+AES128:+SSLv3:!aNULL:!eNULL:!LOW:!3DES:!MD5:!EXP:!PSK:!DSS:
!RC4:!SEED:!IDEA:!ECDSA:kEDH:CAMELLIA128-SHA:AES128-SHA
tls_preempt_cipherlist = yes
tls_ssl_options = NO_COMPRESSION
virtual_alias_maps = mysql:/etc/postfix/sql/aliases.cf
virtual_mailbox_domains = mysql:/etc/postfix/sql/domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/sql/accounts.cf
virtual_transport = lmtp:unix:private/dovecot-lmtp

```

---

### Post by ActionParsnip on 2021-11-08
[https://serverfault.com/questions/718558/helo-command-rejected-host-not-found-setup-postfix-to-accept-sending-mails-fr](https://serverfault.com/questions/718558/helo-command-rejected-host-not-found-setup-postfix-to-accept-sending-mails-fr)

---

### Post by lister171254 on 2021-11-08
I have removed 

reject_unknown_helo_hostname

from main.cf and it now works

```
Nov  9 05:47:27 mail1 postfix/qmgr[1838000]: 1D3D829EC99: removed
Nov  9 05:48:03 mail1 postfix/postscreen[1838380]: CONNECT from [103.151.87.18]:39200 to [xxx.xxx.xxx.xxx]:25
Nov  9 05:48:03 mail1 postfix/postscreen[1838380]: PASS OLD [103.151.87.18]:39200
Nov  9 05:48:05 mail1 postfix/smtpd[1838383]: connect from s2bulkseg.ato.gov.au[103.151.87.18]
Nov  9 05:48:07 mail1 postfix/smtpd[1838383]: BC3E829EC91: client=s2bulkseg.ato.gov.au[103.151.87.18]
Nov  9 05:48:08 mail1 postfix/cleanup[1838259]: BC3E829EC91: message-id=<58ea3199-d72f-4da6-a41d-1cb8b23c4a75@mail.dll>
Nov  9 05:48:11 mail1 postfix/qmgr[1838000]: BC3E829EC91: from=<noreply@mygovid.gov.au>, size=1833, nrcpt=1 (queue active)
Nov  9 05:48:11 mail1 postfix/lmtp[1838204]: BC3E829EC91: to=<leo@mydomain.com>, relay=mail1.mydomain.com[private/dovecot-lmtp], delay=4.5, delays=4.4/0/0/0.07, dsn=2.0.0, status=sent (250 2.0.0 <leo@mydomain.com> CANtMov9iWGcDBwAHQghHA Saved)
Nov  9 05:48:11 mail1 postfix/qmgr[1838000]: BC3E829EC91: removed
Nov  9 05:48:17 mail1 postfix/smtpd[1838383]: disconnect from s2bulkseg.ato.gov.au[103.151.87.18] ehlo=2 starttls=1 mail=1 rcpt=1 data=1 quit=1 commands=7

```

---

### Post by ActionParsnip on 2021-11-09
Please mark as solved if there is no more issue, or provide details if there is still a problem

---

