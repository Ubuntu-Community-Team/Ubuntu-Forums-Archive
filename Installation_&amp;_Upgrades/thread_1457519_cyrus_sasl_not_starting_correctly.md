---
title: "cyrus sasl not starting correctly"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by bluethundr on 2010-04-18
Hello, 

 I am attempting to integrate Cyrus SASL into my mail server but currently am having some difficulty.  I am on Ubuntu Hardy 9.10 Server using a RightScale AWS image.

This is what I see in my postfix logs when I restart sasl

```

Apr 18 17:22:19 domU-12-31-39-0F-7C-53 postfix/smtpd[3741]: warning: SASL per-process initialization failed: generic failure
Apr 18 17:22:19 domU-12-31-39-0F-7C-53 postfix/smtpd[3741]: fatal: SASL per-process initialization failed
Apr 18 17:22:20 domU-12-31-39-0F-7C-53 postfix/master[3644]: warning: process /usr/lib/postfix/smtpd pid 3741 exit status 1
Apr 18 17:22:20 domU-12-31-39-0F-7C-53 postfix/master[3644]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Apr 18 17:23:20 domU-12-31-39-0F-7C-53 postfix/smtpd[3742]: warning: SASL per-process initialization failed: generic failure
Apr 18 17:23:20 domU-12-31-39-0F-7C-53 postfix/smtpd[3742]: fatal: SASL per-process initialization failed
Apr 18 17:23:21 domU-12-31-39-0F-7C-53 postfix/master[3644]: warning: process /usr/lib/postfix/smtpd pid 3742 exit status 1
Apr 18 17:23:21 domU-12-31-39-0F-7C-53 postfix/master[3644]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Apr 18 17:24:21 domU-12-31-39-0F-7C-53 postfix/smtpd[3743]: warning: SASL per-process initialization failed: generic failure
Apr 18 17:24:21 domU-12-31-39-0F-7C-53 postfix/smtpd[3743]: fatal: SASL per-process initialization failed
Apr 18 17:24:22 domU-12-31-39-0F-7C-53 postfix/master[3644]: warning: process /usr/lib/postfix/smtpd pid 3743 exit status 1
Apr 18 17:24:22 domU-12-31-39-0F-7C-53 postfix/master[3644]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

```

These are the lines I've added to my main.cf that seems to have broken my config. Backing up config files, as usual saves the day! :-D

I'll also include a copy of my full config file just in case you would like to have a look see at what works and what doesn't from a comprehensive overview standpoint. 

```

# SASL
smtpd_sasl_auth_enable = yes
# If your potential clients use Outlook Express or other older clients
# this needs to be set to yes
broken_sasl_auth_clients = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
# Add permit_sasl_authenticated to you existing  smtpd_sender_restrictions
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, 
		warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain,
		reject_unauth_pipelining, permit
# Add permit_sasl_authenticated to you existing  smtpd_recipient_restrictions
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, 
		permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, 
		reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit

```

This is what I have set in my /etc/default/saslauthd file. 

```

pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passw :Duk30fZh0u
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1

```

vi /etc/postfix/sasl/smtpd.conf

```

pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passw :xxxxxx
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1

```

---

