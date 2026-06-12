---
title: "smtp works under Hoary, not under Breezy"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by bahbo on 2005-10-16
I have hoary on one partion, and just installed Breezy (kde version) on another partition.  With the Hoary system I can send mail just fine, but I am unable to use postfix to send mail with the Breezy system.  I copied the directory /etc/postfix from Hoary to Breezy, but it still doesn't work.  I believe the problem is in the authentication with the smtp server (sbcglobal.yahoo.com).  In both distributions, I have a file in /etc/postfix/smtp_auth that says:
  [smtp.sbcglobal.yahoo.com]      [email]ricotte@sbcglobal.net[/email]:MYPASSWORD
This works fine under Hoary.
When I try to send mail under Breezy, here is what shows up in /var/log/mail.log

Oct 16 07:12:25 localhost postfix/pickup[9586]: 063C3A3BD7: uid=1000 from=<ric>
Oct 16 07:12:25 localhost postfix/cleanup[9834]: 063C3A3BD7: message-id=<20051016141224.GD8919@otte.ucsc.edu>
Oct 16 07:12:25 localhost postfix/qmgr[9587]: 063C3A3BD7: from=<ric@otte.ucsc.edu>, size=409, nrcpt=1 (queue active)
Oct 16 07:12:25 localhost postfix/smtp[9836]: 063C3A3BD7: to=<ric@phil.ucsc.edu>, relay=smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11], delay=1, status=bounced (host smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11] said: 530 authentication required - for help go to [http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html](http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html) (in reply to MAIL FROM command))
Oct 16 07:12:25 localhost postfix/cleanup[9834]: 5D091A3BD8: message-id=<20051016141225.5D091A3BD8@perelandra>
Oct 16 07:12:25 localhost postfix/qmgr[9587]: 5D091A3BD8: from=<>, size=2349, nrcpt=1 (queue active)
Oct 16 07:12:25 localhost postfix/qmgr[9587]: 063C3A3BD7: removed
Oct 16 07:12:25 localhost postfix/smtp[9836]: 5D091A3BD8: to=<ric@otte.ucsc.edu>, relay=smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11], delay=0, status=bounced (host smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11] said: 530 authentication required - for help go to [http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html](http://help.yahoo.com/help/us/sbc/dsl/mail/pop/pop-11.html) (in reply to MAIL FROM command))
Oct 16 07:12:25 localhost postfix/qmgr[9587]: 5D091A3BD8: removed

When I send mail under hoary, I get something like:

Oct 15 11:20:04 localhost postfix/pickup[7356]: 72C1F1039B: uid=1000
from=<ric>
Oct 15 11:20:04 localhost postfix/cleanup[8007]: 72C1F1039B:
message-id=<20051015182004.GA7867@otte.ucsc.edu>
Oct 15 11:20:04 localhost postfix/qmgr[7357]: 72C1F1039B:
from=<ric@otte.ucsc.edu>, size=425, nrcpt=1 (queue active)
Oct 15 11:20:04 localhost postfix/smtp[8009]: warning: database
/etc/postfix/smtp_auth.db is older than source file /etc/postfix/smtp_auth
Oct 15 11:20:05 localhost postfix/smtp[8009]: 72C1F1039B:
to=<ric@phil.ucsc.edu>, relay=smtp.sbcglobal.yahoo.com[68.142.198.11],
delay=1, status=sent (250 ok 1129400405 qp 17374)
Oct 15 11:20:05 localhost postfix/qmgr[7357]: 72C1F1039B: removed

So it looks like the authentication at the smtp server is failing, but I don't see why it would work under Hoary and not under Breezy.  My /etc/posfix/main.cf file is:


smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no
append_dot_mydomain = no
home_mailbox = Maildir/
mailbox_command = /usr/bin/procmail
myhostname = perelandra
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydomain = perelandra
mydestination = $myhostname, localhost.$mydomain, $mydomain, localhost
relayhost = [smtp.sbcglobal.yahoo.com]
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/smtp_auth
smtp_sasl_security_options = noanonymous
unknown_local_recipient_reject_code = 450
mynetworks = 127.0.0.0/8

Any help would be appreciated.  Thanks,

Ric

---

### Post by bahbo on 2005-10-17
Hi,
I found a solution to this problem.  As root, run
   postmap /etc/postfix/smpt_auth
and then
   postfix reload
Now mail is sent just fine,
Ric

---

### Post by WheelDweller on 2006-09-10
Point of order:

The command line you meant to type was:
 postmap /etc/postfix/smtp_auth  (typo)

Just help out, that's all.

Dapper has the same kinda situation; I looked all over the place before I found your post- thanks!

---

