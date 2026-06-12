---
title: "Postfix SMTP Authentication Problem"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by bobster_b on 2007-11-06
Hello.  I've been using the docs at [http://flurdy.com/docs/postfix](http://flurdy.com/docs/postfix) to set up postfix.

I'm unable to authenticate to SMTP using any method.

I am able to connect via my local network (because of the my_networks param) without auth.

I see all of the following in my mail.log (have postfix set to log verbosely), but at the same time I never see a lookup take place in the mysql log (which is also running full time).

IMAP auth works fine.

At my wits end.  I've looked at 50 different things.  I'm amazed I haven't killed postfix yet.

Below are my mail.log for a connection and my main.cf

Thanks, Heath



OUTPUT FROM mail.log

[INDENT]Nov  6 20:01:58 tiki postfix/smtpd[8834]: connection established
Nov  6 20:01:58 tiki postfix/smtpd[8834]: master_notify: status 0
Nov  6 20:01:58 tiki postfix/smtpd[8834]: name_mask: resource
Nov  6 20:01:58 tiki postfix/smtpd[8834]: name_mask: software
Nov  6 20:01:58 tiki postfix/smtpd[8834]: name_mask: noanonymous
Nov  6 20:02:02 tiki postfix/smtpd[8834]: connect from unknown[10.0.0.4]
Nov  6 20:02:02 tiki postfix/smtpd[8834]: match_list_match: unknown: no match
Nov  6 20:02:02 tiki postfix/smtpd[8834]: match_list_match: 10.0.0.4: no match
Nov  6 20:02:02 tiki postfix/smtpd[8834]: match_list_match: unknown: no match
Nov  6 20:02:02 tiki postfix/smtpd[8834]: match_list_match: 10.0.0.4: no match
Nov  6 20:02:02 tiki postfix/smtpd[8834]: match_hostname: unknown ~? 10.0.0.0/24
Nov  6 20:02:02 tiki postfix/smtpd[8834]: match_hostaddr: 10.0.0.4 ~? 10.0.0.0/24
Nov  6 20:02:02 tiki postfix/smtpd[8834]: > unknown[10.0.0.4]: 220 tiki.tallbob.com ESMTP Postfix
Nov  6 20:02:02 tiki postfix/smtpd[8834]: < unknown[10.0.0.4]: EHLO [10.0.0.4]
Nov  6 20:02:02 tiki postfix/smtpd[8834]: > unknown[10.0.0.4]: 250-tiki.tallbob.com
Nov  6 20:02:02 tiki postfix/smtpd[8834]: > unknown[10.0.0.4]: 250-PIPELINING
Nov  6 20:02:02 tiki postfix/smtpd[8834]: > unknown[10.0.0.4]: 250-SIZE 10240000
Nov  6 20:02:02 tiki postfix/smtpd[8834]: > unknown[10.0.0.4]: 250-ETRN
Nov  6 20:02:02 tiki postfix/smtpd[8834]: > unknown[10.0.0.4]: 250-AUTH LOGIN PLAIN DIGEST-MD5 CRAM-MD5
Nov  6 20:02:02 tiki postfix/smtpd[8834]: match_list_match: unknown: no match
Nov  6 20:02:02 tiki postfix/smtpd[8834]: match_list_match: 10.0.0.4: no match
Nov  6 20:02:02 tiki postfix/smtpd[8834]: > unknown[10.0.0.4]: 250-AUTH=LOGIN PLAIN DIGEST-MD5 CRAM-MD5
Nov  6 20:02:02 tiki postfix/smtpd[8834]: > unknown[10.0.0.4]: 250 8BITMIME
Nov  6 20:02:02 tiki postfix/smtpd[8834]: < unknown[10.0.0.4]: AUTH PLAIN AGh2b2xtZXJAZGlnaXRhbGRvbWFpbnN5c3RlbXMuY29tAGJvYjE5OTVib28=
Nov  6 20:02:02 tiki postfix/smtpd[8834]: smtpd_sasl_authenticate: sasl_method PLAIN, init_response AGh2b2xtZXJAZGlnaXRhbGRvbWFpbnN5c3RlbXMuY29tAGJvYjE5OTVib28=
Nov  6 20:02:02 tiki postfix/smtpd[8834]: smtpd_sasl_authenticate: decoded initial response 
Nov  6 20:02:02 tiki postfix/smtpd[8834]: warning: SASL authentication failure: Password verification failed
Nov  6 20:02:02 tiki postfix/smtpd[8834]: warning: unknown[10.0.0.4]: SASL PLAIN authentication failed
Nov  6 20:02:02 tiki postfix/smtpd[8834]: > unknown[10.0.0.4]: 535 Error: authentication failed
Nov  6 20:02:02 tiki postfix/smtpd[8834]: smtp_get: EOF
Nov  6 20:02:02 tiki postfix/smtpd[8834]: match_hostname: unknown ~? 10.0.0.0/24
Nov  6 20:02:02 tiki postfix/smtpd[8834]: match_hostaddr: 10.0.0.4 ~? 10.0.0.0/24
Nov  6 20:02:02 tiki postfix/smtpd[8834]: lost connection after AUTH from unknown[10.0.0.4]
Nov  6 20:02:02 tiki postfix/smtpd[8834]: disconnect from unknown[10.0.0.4]
Nov  6 20:02:02 tiki postfix/smtpd[8834]: master_notify: status 1
Nov  6 20:02:02 tiki postfix/smtpd[8834]: connection closed
Nov  6 20:02:05 tiki postfix/smtpd[8829]: smtp_get: EOF
Nov  6 20:02:05 tiki postfix/smtpd[8829]: match_hostname: pool-71-127-23-172.trrhin.dsl-w.verizon.net ~? 10.0.0.0/24
Nov  6 20:02:05 tiki postfix/smtpd[8829]: match_hostaddr: 71.127.23.172 ~? 10.0.0.0/24
Nov  6 20:02:05 tiki postfix/smtpd[8829]: match_list_match: pool-71-127-23-172.trrhin.dsl-w.verizon.net: no match
Nov  6 20:02:05 tiki postfix/smtpd[8829]: match_list_match: 71.127.23.172: no match
Nov  6 20:02:05 tiki postfix/smtpd[8829]: send attr request = disconnect
Nov  6 20:02:05 tiki postfix/smtpd[8829]: send attr ident = smtp:71.127.23.172
Nov  6 20:02:05 tiki postfix/smtpd[8829]: private/anvil: wanted attribute: status
Nov  6 20:02:05 tiki postfix/smtpd[8829]: input attribute name: status
Nov  6 20:02:05 tiki postfix/smtpd[8829]: input attribute value: 0
Nov  6 20:02:05 tiki postfix/smtpd[8829]: private/anvil: wanted attribute: (list terminator)
Nov  6 20:02:05 tiki postfix/smtpd[8829]: input attribute name: (end)
Nov  6 20:02:05 tiki postfix/smtpd[8829]: lost connection after MAIL from pool-71-127-23-172.trrhin.dsl-w.verizon.net[71.127.23.172]
Nov  6 20:02:05 tiki postfix/smtpd[8829]: disconnect from pool-71-127-23-172.trrhin.dsl-w.verizon.net[71.127.23.172]
Nov  6 20:02:05 tiki postfix/smtpd[8829]: master_notify: status 1
Nov  6 20:02:05 tiki postfix/smtpd[8829]: connection closed[/INDENT]


MY main.cf

[INDENT]# See /usr/share/postfix/main.cf.dist for a commented, more complete version

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_use_tls=yes
#smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = tiki.tallbob.com
#alias_maps = hash:/etc/aliases
#alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = tallbob.com, tiki.domain.actdsltmp, localhost.domain.actdsltmp, localhost
relayhost =
mynetworks = 10.0.0.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


local_recipeint_maps =
mydestination =

# how long if undelivered before sending warning update to sender
delay_warning_time = 4h

# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450

# how long to keep message on queue before return as failed.
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
maximal_queue_lifetime = 7d
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s

# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s

# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 16

# how many error before back off.
smtpd_soft_error_limit = 3

# how many max errors before blocking it.
smtpd_hard_error_limit = 12

# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hos$

# Requirements for the sender details
smtpd_sender_restrictions = permit_mynetworks, permit_sasl_authenticated, warn_if_reject reject_non_fqdn$

# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, rejec$

# Requirement for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, r$

# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases

# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and their user id
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
# and group id
virtual_gid_maps =  mysql:/etc/postfix/mysql_gid.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

smtpd_sasl_auth_enable = yes
smtpd_sasl2_auth_enable = yes
#smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
broken_sasl_auth_clients = yes
[/INDENT]

---

### Post by renbaoru on 2008-01-03
Were you able to fix this?  I'm having the same problem and I used the same Flurdy setup as you.

My SASL AUTH problems started after I did
```
sudo apt-get update
sudo apt-get upgrade
```
And I believe postfix was in the upgrade packages.

Thanks!

---

### Post by bobster_b on 2008-01-03
Actually I did get it fixed and frankly I have no idea what I did (it has been a while.)  I sort of recall removing everything that the Flurdy doc had me install, except for the databases, and starting over.  I really wish I could help more.

---

