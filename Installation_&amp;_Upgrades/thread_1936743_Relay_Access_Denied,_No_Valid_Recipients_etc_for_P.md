---
title: "Relay Access Denied, No Valid Recipients etc for Postfix Email setup Pls Help!"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by unixaunixa on 2012-03-06
Hi,

I am desperate I have spent three weeks trying to set up my email server on my hosted ubuntu server and cannot send email! I used the ubuntu how-to setup guides and also set up my MX entries using DNS.

I can do "telnet locahost 25" and email successfully, but cannot send email from outside clients! Pls help me. I am desperate at this point and need the email for my company.

Pls let me know which configuration files I should post. I looked at various other forums and tried the tips, but nothing has resolved the issue for me. I am using shadow authentication for user accounts. Ubuntu 10.04.2 using Postfix w/saslauthd

Thanks,

U

Errors:

The original message was received at Tue, 6 Mar 2012 13:38:26 -0500 (EST) from localhost [127.0.0.1] ----- The following addresses had permanent fatal errors ----- <queen@myserver.com> (reason: 554 5.7.1 <queen@myserver.com>: Relay access denied) ----- Transcript of session follows ----- ... while talking to mail.myserver.com.: >>> DATA <<< 554 5.7.1 <queen@myserver.com>: Relay access denied 554 5.0.0 Service unavailable <<< 554 5.5.1 Error: no valid recipients

---

### Post by wyliecoyoteuk on 2012-03-06
You will need to post more information I'm afraid.
Pretty obvious that jmc-worldwide server is not set to allow relay messages from the client.

Could be lots of reasons for that, but as you don't say where the error is from, or what the client or email server are, it is all a bit moot.

If you are trying to send email from an internal network to the internet, you will need to permit relaying from local clients, I think it is disabled by default in Postfix.

This doc might give you some clues

[http://www.answersthatwork.com/Download_Area/ATW_Library/Networking/Network__3-SMTP_Server_Status_Codes_and_SMTP_Error_Codes.pdf](http://www.answersthatwork.com/Download_Area/ATW_Library/Networking/Network__3-SMTP_Server_Status_Codes_and_SMTP_Error_Codes.pdf)

---

### Post by unixaunixa on 2012-03-06
> **wyliecoyoteuk said:**
> You will need to post more information I'm afraid.
Pretty obvious that myserver server is not set to allow relay messages from the client.

Could be lots of reasons for that, but as you don't say where the error is from, or what the client or email server are, it is all a bit moot.

If you are trying to send email from an internal network to the internet, you will need to permit relaying from local clients, I think it is disabled by default in Postfix.

This doc might give you some clues

[http://www.answersthatwork.com/Download_Area/ATW_Library/Networking/Network__3-SMTP_Server_Status_Codes_and_SMTP_Error_Codes.pdf](http://www.answersthatwork.com/Download_Area/ATW_Library/Networking/Network__3-SMTP_Server_Status_Codes_and_SMTP_Error_Codes.pdf)
Thanks for responding! Perhaps the following details may assist.

1. Where the error is from? Emailing to the address from an external email web client. It also fails when I use netcat. Example:
...
netcat mail.myserver.com 25
220 s15343205.onlinehome-server.com ESMTP Postfix
ehlo myserver.com
250-s15343205.onlinehome-server.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN DIGEST-MD5 CRAM-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from: [email]root@myserver.com[/email]
250 2.1.0 Ok
rcpt to: [email]queen@myserver.com[/email]
554 5.7.1 <queen@myserver.com>: Relay access denied
...

2. Email server is Postfix email server. See main.cf below.

...................................................................................... begin main.cf
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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.myserver.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.myserver.com, localhost.localdomain, localhost, myserver.com, s15343214.onlinehome-server.com
relayhost =
mynetworks = 127.0.0.0/8,74.208.11.193/25,192.168.1.0/24
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
...................................................................................... end main.cf

---

