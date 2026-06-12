---
title: "Amavisd-new - emails going to deferred"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by 2byakin on 2010-04-23
new at ubuntu
 
Ubuntu 9.1
 
Upgraded to version 9.1.  finally got it all to load.  I think amavisd is runing but not sure.  Here is some output.
 
# dpkg -l | grep amavis
ii  amavisd-new                               1:2.6.4-1ubuntu3                        Interface between MTA and virus scanner/cont

 
 
# telnet localhost 10024
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

# cat main.cf
message_size_limit = 102400000
mailbox_size_limit = 102400000
smtpd_helo_required = yes
disable_vrfy_command = yes
mydomain = xante.com
myhostname = mx2.xante.com
proxy_interfaces = 66.255.189.165
unknown_local_recipient_reject_code = 550
relay_domains = /etc/postfix/relay_domains
transport_maps = hash:/etc/postfix/transport.map
smtpd_banner = $myhostname ESMTP
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mailbox_command = procmail -a "$EXTENSION"
inet_interfaces = all
append_dot_mydomain = no
biff = no
recipient_delimiter = +
header_checks = regexp:/etc/postfix/header_checks
content_filter = smtp-amavis:[127.0.0.1]:10024
#maximal_queue_lifetime = 2d

 
 
Below is the main part of master.cf
 
spamassassin unix -     n       n       -       -       pipe
        user=nobody argv=/usr/bin/spamc -f -e
        /usr/sbin/sendmail -oi -f${sender} ${recipient}
 
smtp-amavis     unix    -       -       -       -       2       smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20
 
127.0.0.1:10025 inet    n       -       -       -       -       smtpd
        -o content_filter=spamassassin
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_delay_reject=no
        -o smtpd_client_restrictions=permit_mynetworks,reject
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o smtpd_data_restrictions=reject_unauth_pipelining
        -o smtpd_end_of_data_restrictions=
        -o mynetworks=127.0.0.0/8
        -o smtpd_error_sleep_time=0
        -o smtpd_soft_error_limit=1001
        -o smtpd_hard_error_limit=1000
        -o smtpd_client_connection_count_limit=0
        -o smtpd_client_connection_rate_limit=0
        -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
 
I don't see a file named amavisd.conf that I have read others talk about.  
 
Please help.  Email is coming in and sitting in deferred queue.  If I run postsuper -r ALL, the email does then go to the users accounts.

---

### Post by 2byakin on 2010-04-23
Not sure if this helps
 
# amavisd-new stop
The amavisd daemon is apparently not running, no PID file /var/run/amavis/amavisd.pid
# amavisd-new start
#
 
 
If I enter the amavisd-new start, it doesn't say it starts, it just comes back to the # prompt
 
I don't have a /var/run/amavis folder

---

### Post by 2byakin on 2010-04-23
Another item.
 
I was runing Gutsy version and all was working fine until found out the hard way that clamav version I was using expired on 4/15/10.  I finally got the update to ubuntu version 9.10.  I did not do a clean install, just upgraded one version at a time.

---

### Post by 2byakin on 2010-04-26
Solved.  used following command
 
amavisd reload

---

