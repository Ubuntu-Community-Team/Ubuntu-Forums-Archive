---
title: "Postfix error (EC2)"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by Derleek on 2009-11-20
Hi,

I'm in the process of setting up a mail server (Postfix) on an amazon EC2 server.  I am using a [Bitnami/Moodle]("http://developer.amazonwebservices.com/connect/entry.jspa?externalID=2921") instance.  Which runs Ubuntu 9.04.

I'm using [this]("http://flurdy.com/docs/postfix/") guide and got to the end of the [configuration]("http://flurdy.com/docs/postfix/#config-extra-admin") section, at which point the guide tells me to test the server before going any further.

Not knowing the proper way to do this, I looked up [this]("http://beginlinux.com/server_training/mail-server/1041-postfix-mail-server-set-up") additional guide.  Which instructed me to "send a test message to root".

Like so - 
[COLOR=#0000ff][FONT=Arial, sans-serif][SIZE=2]**[COLOR=#000000]#[/COLOR] echo test | /usr/sbin/sendmail -f root root**[/SIZE][/FONT][/COLOR]
 
  [COLOR=#0000ff][FONT=Arial, sans-serif][SIZE=2][B]tail  /var/log/mail.log

[/B][/SIZE][/FONT][/COLOR]**When looking at the mail.log file I found the following messages:**

Nov 17 20:04:10 (none) postfix/qmgr[26515]: DD9F1628C4: from=<[EMAIL="root@drugawarenesseducation.com"]root@drugawarenesseducation.com[/EMAIL]>, size=300, nrcpt=3 (queue active)

Nov 17 20:04:11 (none) postfix/smtp[18772]: DD9F1628C4: host [smtp.secureserver.net]("http://smtp.secureserver.net/")[216.69.186.201] refused to talk to me: 554-m1pismtp01-020.prod.$

Nov 17 20:04:14 (none) postfix/smtp[18772]: DD9F1628C4: to=<[EMAIL="/var/log/mail.log@drugawarenesseducation.com"]/var/log/mail.log@drugawarenesseducation.com[/EMAIL]>, orig_to=</var/log/mail.log>, relay=mail$

Nov 17 20:04:14 (none) postfix/smtp[18772]: DD9F1628C4: to=<[EMAIL="root@drugawarenesseducation.com"]root@drugawarenesseducation.com[/EMAIL]>, orig_to=<root>, relay=[mailstore1.secureserver.net]("http://mailstore1.secureserver.net/")[72$

Nov 17 20:04:14 (none) postfix/smtp[18772]: DD9F1628C4: to=<[EMAIL="tail@drugawarenesseducation.com"]tail@drugawarenesseducation.com[/EMAIL]>, orig_to=<tail>, relay=[mailstore1.secureserver.net]("http://mailstore1.secureserver.net/")[72$

This appeared to run over night because I got a message from amazon (basically) saying "You've reached the limit of email you can send on this instance, please send a request if you'd like to remove this limit"

__

I have opened ports - 25,143,465,587, 993, 80 and 443

According to the first guide's section concerning [ec2 use]("http://flurdy.com/docs/postfix/#ec2_use"), it is likely that certain spam filters will catch my IP (ex: [spamhaus]("http://www.spamhaus.org/")).  Under which it says that my ability to send mail is restricted by AWS (who has not contacted me back... grr).

Anyways... any and all tips/advice on handling this dilemma would be greatly appreciated.

Thanks.

---

### Post by Derleek on 2009-11-20
Still no response from Amazon... I'll update when i get one.

---

