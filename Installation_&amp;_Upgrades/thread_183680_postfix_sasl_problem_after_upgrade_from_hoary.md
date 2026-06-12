---
title: "postfix sasl problem after upgrade from hoary"
date: 2006-05-28
forum: Installation &amp; Upgrades
---

### Post by eelliott on 2006-05-28
I'm running postfix locally as an external mail relay on my ubuntu system. I have it configured to relay mail through my dsl provider at smtp.sbcglobal.yahoo.com.  SBC/Yahoo requires sasl authentication to send, so I enabled smtp sasl and made a password database.  Everything works fine on ubuntu/hoary with postfix 2.1.5.

I just upgraded to ubuntu/breezy which has postfix 2.2.4.  After the upgrade, postfix accepts mail ine but won't use sasl when it relays outbound mail.  Here are the log messages:

BEFORE (working)
May 21 10:08:45 morbo postfix/smtp[5103]: C3E9522FA1: to=<XXX@gmail.com>, relay=smtp.sbcglobal.yahoo.com[68.142.198.11], delay=2, status=sent (250 ok 1148231428 qp 26813)

AFTER (broken)
May 28 00:50:40 morbo postfix/smtp[9176]: 67E2D195FF: to=<XXX@gmail.com>, relay=smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11], delay=0, status=undeliverable (delivery via smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11]: host smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11] said: 530 authentication required - for help go to [http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html](http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html) (in reply to MAIL FROM command))

which is the same log message I saw before enabling sasl when I first setup postfix last year.  The 530 url is just a page about setting up SASL auth in your smtp client.  Everything else in the logs looks normal, no errors or warnings of any kind on startup.  My config files are virtually unchanged (see below) and tls support is built-in to the postfix package in breezy (no separate postfix-tls package anymore).  I've rebuilt the transport and sasl databases with postmap and restarted the postfix daemon, but nothing changes.

Can anyone shed some light on why sasl stopped working?  What changed between versions 2.1 and 2.2?  Or is something else going on?

I diffed my current config files against the original working ones.  The only differences are a couple new lines in master.cf, which I never touched.  If I downgrade to postfix 2.1, sasl relaying works with these same config files.

==========================
$ diff -u master.cf /old-root/etc/postfix/
- master.cf   2006-05-28 01:05:06.000000000 -0700
+ /old-root/etc/postfix/master.cf     2005-07-30 22:21:27.000000000 -0700
@@ -122,7 +122,3 @@
 #tlsmgr          fifo  -       -       n       300     1       tlsmgr
 #smtps   inet  n       -       n       -       -       smtpd -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes
 #587     inet  n       -       n       -       -       smtpd -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes
-# added by breezy
-#tlsmgr    unix  -       -       -       1000?   1       tlsmgr
-#scache    unix  -       -       -       -       1       scache
-#discard   unix  -       -       -       -       -       discard

==========================
$ cat main.cf

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

myhostname = XXX.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = localhost.localdomain, localhost, XXX.org

# default, send directly to recipient's mail server
relayhost =
# lookup relay in table
transport_maps = hash:/etc/postfix/transport

mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only

# SBC requires auth for relaying
smtp_sasl_auth_enable = yes
# SBC auth is plaintext, blank to clear
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
 
==========================
$ grep -v "^#" transport
localhost      :
.localdomain   :
XXX.org        :
*              relay:[smtp.sbcglobal.yahoo.com]

==========================
$ grep -v "^#" sasl_passwd
smtp-sbc.mail.yahoo.com         NAME:PASS

Thanks for your help.

---

### Post by eelliott on 2006-05-28
I've gotten it working again thanks to some help from the postfix newsgroups.  It appears postfix 2.2.4 is translating the bracketed transport name smtp.sbcglobal.yahoo.com into the CNAME smtp.sbc.mail.yahoo4.akadns.net.  The brackets are supposed to prevent this, but they aren't for some reason.  Adding an entry to sasl_passwd for smtp.sbc.mail.yahoo4.akadns.net fixes it for now.

---

### Post by jabster on 2006-06-21
> The brackets are supposed to prevent this, but they aren't for some reason

I was having the same problem as you (why are the SBC smtp servers consistently such a PITA?). All worked fine on my gentoo box, but then not on a fresh kubuntu dapper server install. Adding that extra server got it working.

what was the end result of the mailing list discussion? Bug in postfix?

thx,
john

---

