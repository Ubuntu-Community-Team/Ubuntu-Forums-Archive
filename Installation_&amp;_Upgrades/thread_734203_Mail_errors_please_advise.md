---
title: "Mail errors please advise"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by IzaKamakazi on 2008-03-24
Hi Guys,

I have recently installed Gutsy gibbon server edition with all the initial option selected during the install.All went well and I had my website up and running in no time.

I then decided to use Postfix to run a mail server, again the basic mail server ran fine with incoming and outgoing mail. My problems started when I tried to follow this tutorial ( [http://fieldyweb.co.uk/blog/?p=548](http://fieldyweb.co.uk/blog/?p=548) ) to set up SSL.

All seemed to be going ok untill i reached:

Now start saslauthd:

/etc/init.d/saslauthd start

To see if SMTP-AUTH and TLS work properly now run the following command:

telnet localhost 25

When I telnet port 25 I get the following error:

telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

At this point it freezes and any input seems to be ignored i.e ehlo localhost so I cannot continue with the installation.I have tried a few cut and paste tutorials but they all give me the same result.this question has been asked before but unfortunatly it was never resolved.

here is the results of netstat -l | grep tcp

tcp 0 0 *:20000 *:* LISTEN
tcp 0 0 *:imaps *:* LISTEN
tcp 0 0 *op3s *:* LISTEN
tcp 0 0 localhost:10026 *:* LISTEN
tcp 0 0 localhost:mysql *:* LISTEN
tcp 0 0 *:netbios-ssn *:* LISTEN
tcp 0 0 *op3 *:* LISTEN
tcp 0 0 *:imap2 *:* LISTEN
tcp 0 0 *:webmin *:* LISTEN
tcp 0 0 *:www *:* LISTEN
tcp 0 0 webserver.local:domain *:* LISTEN
tcp 0 0 localhost:domain *:* LISTEN
tcp 0 0 localhost:ipp *:* LISTEN
tcp 0 0 localhostostgresql *:* LISTEN
tcp 0 0 *:smtp *:* LISTEN
tcp 0 0 localhost:953 *:* LISTEN
tcp 0 0 *:microsoft-ds *:* LISTEN
tcp6 0 0 *:ftp *:* LISTEN
tcp6 0 0 *:domain *:* LISTEN
tcp6 0 0 *:ssh *:* LISTEN
tcp6 0 0 *:smtp *:* LISTEN
tcp6 0 0 ip6-localhost:953 *:* LISTEN

As things stand I can send mail but not receive. Here is an extract from /var/log/mail.log

Mar 24 00:07:03 webserver postfix/master[5586]: daemon started -- version 2.4.5, configuration /etc/postfix
Mar 24 00:07:10 webserver postfix/smtpd[5898]: warning: SASL per-process initialization failed: generic failure
Mar 24 00:07:10 webserver postfix/smtpd[5898]: fatal: SASL per-process initialization failed
Mar 24 00:07:11 webserver postfix/master[5586]: warning: process /usr/lib/postfix/smtpd pid 5898 exit status 1
Mar 24 00:07:11 webserver postfix/master[5586]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Mar 24 00:07:18 webserver dovecot: Dovecot v1.0.5 starting up

Here is my /etc/postfix/main.cf

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
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
smtpd_tls_session_cache_database=btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database=btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = iza-games.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = iza-games.co.uk, webserver.home, localhost.home, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command=procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
ignore_mx_lookup_error = yes
smtp_connect_timeout = 300s
fallback_relay =
smtpd_helo_required = yes


Here is my /etc/postfix/master.cf

#
# Postfix master process configuration file. For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# ==========================================================================
# service type private unpriv chroot wakeup maxproc command + args
# (yes) (yes) (yes) (never) (100)
# ==========================================================================
smtp inet n - - - - smtpd
#submission inet n - - - - smtpd
# -o smtpd_enforce_tls=yes
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#smtps inet n - - - - smtpd
# -o smtpd_tls_wrappermode=yes
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#628 inet n - - - - qmqpd
pickup fifo n - - 60 1 pickup
cleanup unix n - - - 0 cleanup
qmgr fifo n - n 300 1 qmgr
#qmgr fifo n - - 300 1 oqmgr
tlsmgr unix - - - 1000? 1 tlsmgr
rewrite unix - - - - - trivial-rewrite
bounce unix - - - - 0 bounce
defer unix - - - - 0 bounce
trace unix - - - - 0 bounce
verify unix - - - - 1 verify
flush unix n - - 1000? 0 flush
proxymap unix - - n - - proxymap
smtp unix - - - - - smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay unix - - - - - smtp
-o smtp_fallback_relay=
# -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq unix n - - - - showq
error unix - - - - - error
retry unix - - - - - error
discard unix - - - - - discard
local unix - n n - - local
virtual unix - n n - - virtual
lmtp unix - - - - - lmtp
anvil unix - - - - 1 anvil
scache unix - - - - 1 scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent. See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop unix - n n - - pipe
flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp unix - n n - - pipe
flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail unix - n n - - pipe
flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp unix - n n - - pipe
flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix - n n - 2 pipe
flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman unix - n n - - pipe
flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
${nexthop} ${user}


I have tried the reinstall of gutsy mant times but it hasn't helped.

I am totally lost in where I should go from here.

Can anyone point me in the right direction, I think 3 days is long enough without seeking help LOL.

Many thanks for your input.

Kamakazi.

---

### Post by IzaKamakazi on 2008-03-26
*Bump*

Any idea's anyone?

Cheers

---

