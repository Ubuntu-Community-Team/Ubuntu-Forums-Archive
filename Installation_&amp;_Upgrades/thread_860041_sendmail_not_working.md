---
title: "sendmail not working"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by SpikeyMike on 2008-07-15
Hi
I created a php file with a mail() function and am trying to use it to send mail, I installed sendmail and configured the php.ini file as shown here:

[COLOR="Red"][I][SIZE="2"]; For Unix only. You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t -i[/SIZE][/I][/COLOR]

but when I try to send mail it doesn't work, I also tried installing postfix (which uninstalled sendmail) and edited /etc/postfix/main.cf and put my correct external smtp server in there

relayhost = smtp.orange.nl

but this doesn't work either

here are the last few entries in the mail.log file, any help greatly appreciated

Spikey

[I][COLOR="Red"]Jul 14 22:00:40 Ubuntu sendmail[15533]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:01:40 Ubuntu sendmail[15533]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:01:40 Ubuntu sendmail[15533]: alias database /etc/mail/aliases rebuilt by root
Jul 14 22:01:40 Ubuntu sendmail[15533]: /etc/mail/aliases: 1 aliases, longest 5 bytes, 9 bytes total
Jul 14 22:01:41 Ubuntu sm-mta[15586]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:01:43 Ubuntu sm-msp-queue[15591]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:02:41 Ubuntu sm-mta[15586]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:02:41 Ubuntu sm-mta[15627]: starting daemon (8.14.2): SMTP+queueing@00:10:00
Jul 14 22:02:43 Ubuntu sm-msp-queue[15591]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:10:38 Ubuntu sendmail[15723]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:11:38 Ubuntu sendmail[15723]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:11:38 Ubuntu sendmail[15723]: m6EKBcJn015723: from=www-data, size=91, class=0, nrcpts=1, msgid=<200807142011.m6EKBcJn015723@Ubuntu>, relay=www-data@localhost
Jul 14 22:11:38 Ubuntu sm-mta[15725]: m6EKBc8S015725: from=<www-data@Ubuntu>, size=300, class=0, nrcpts=1, msgid=<200807142011.m6EKBcJn015723@Ubuntu>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Jul 14 22:11:38 Ubuntu sendmail[15723]: m6EKBcJn015723: to=michael562706@hotmail.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30091, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m6EKBc8S015725 Message accepted for delivery)
Jul 14 22:11:38 Ubuntu sendmail[15729]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:12:38 Ubuntu sendmail[15729]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:12:39 Ubuntu sendmail[15729]: m6EKCcNu015729: from=www-data, size=91, class=0, nrcpts=1, msgid=<200807142012.m6EKCcNu015729@Ubuntu>, relay=www-data@localhost
Jul 14 22:12:39 Ubuntu sm-mta[15733]: m6EKCdOv015733: from=<www-data@Ubuntu>, size=300, class=0, nrcpts=1, msgid=<200807142012.m6EKCcNu015729@Ubuntu>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Jul 14 22:12:39 Ubuntu sendmail[15729]: m6EKCcNu015729: to=mikeinamsterdam@gmail.com, ctladdr=www-data (33/33), delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=30091, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m6EKCdOv015733 Message accepted for delivery)
Jul 14 22:12:39 Ubuntu sendmail[15737]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:13:08 Ubuntu sendmail[15741]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:13:39 Ubuntu sendmail[15737]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:13:39 Ubuntu sendmail[15737]: m6EKDdxx015737: from=www-data, size=92, class=0, nrcpts=1, msgid=<200807142013.m6EKDdxx015737@Ubuntu>, relay=www-data@localhost
Jul 14 22:13:39 Ubuntu sm-mta[15743]: m6EKDddS015743: from=<www-data@Ubuntu>, size=301, class=0, nrcpts=1, msgid=<200807142013.m6EKDdxx015737@Ubuntu>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Jul 14 22:13:39 Ubuntu sendmail[15737]: m6EKDdxx015737: to=mikeyinamsterdam@gmail.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30092, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m6EKDddS015743 Message accepted for delivery)
Jul 14 22:13:39 Ubuntu sendmail[15747]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:14:08 Ubuntu sendmail[15741]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:14:08 Ubuntu sendmail[15741]: m6EKE8Fc015741: from=www-data, size=91, class=0, nrcpts=1, msgid=<200807142014.m6EKE8Fc015741@Ubuntu>, relay=www-data@localhost
Jul 14 22:14:09 Ubuntu sm-mta[15748]: m6EKE8ea015748: from=<www-data@Ubuntu>, size=300, class=0, nrcpts=1, msgid=<200807142014.m6EKE8Fc015741@Ubuntu>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Jul 14 22:14:09 Ubuntu sendmail[15741]: m6EKE8Fc015741: to=michael562706@hotmail.com, ctladdr=www-data (33/33), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30091, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m6EKE8ea015748 Message accepted for delivery)
Jul 14 22:14:09 Ubuntu sendmail[15752]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:14:37 Ubuntu sendmail[15759]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:14:39 Ubuntu sendmail[15747]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:15:09 Ubuntu sendmail[15752]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:15:09 Ubuntu sendmail[15752]: m6EKF9oj015752: from=www-data, size=91, class=0, nrcpts=1, msgid=<200807142015.m6EKF9oj015752@Ubuntu>, relay=www-data@localhost
Jul 14 22:15:09 Ubuntu sm-mta[15763]: m6EKF9ER015763: from=<www-data@Ubuntu>, size=300, class=0, nrcpts=1, msgid=<200807142015.m6EKF9oj015752@Ubuntu>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Jul 14 22:15:09 Ubuntu sendmail[15752]: m6EKF9oj015752: to=mikeinamsterdam@gmail.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30091, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m6EKF9ER015763 Message accepted for delivery)
Jul 14 22:15:09 Ubuntu sendmail[15767]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:15:18 Ubuntu sm-mta[15735]: m6EKCdOv015733: to=<mikeinamsterdam@gmail.com>, ctladdr=<www-data@Ubuntu> (33/33), delay=00:02:39, xdelay=00:02:39, mailer=esmtp, pri=120300, relay=gsmtp147.google.com. [209.185.147.27], dsn=4.0.0, stat=Deferred: gsmtp147.google.com.: No route to host
Jul 14 22:15:37 Ubuntu sendmail[15759]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:15:37 Ubuntu sendmail[15759]: m6EKFbYj015759: from=www-data, size=91, class=0, nrcpts=1, msgid=<200807142015.m6EKFbYj015759@Ubuntu>, relay=www-data@localhost
Jul 14 22:15:37 Ubuntu sm-mta[15771]: m6EKFbnp015771: from=<www-data@Ubuntu>, size=300, class=0, nrcpts=1, msgid=<200807142015.m6EKFbYj015759@Ubuntu>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Jul 14 22:15:37 Ubuntu sendmail[15759]: m6EKFbYj015759: to=michael562706@hotmail.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30091, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m6EKFbnp015771 Message accepted for delivery)
Jul 14 22:15:37 Ubuntu sendmail[15775]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:16:09 Ubuntu sendmail[15767]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:16:09 Ubuntu sendmail[15767]: m6EKG93u015767: from=www-data, size=92, class=0, nrcpts=1, msgid=<200807142016.m6EKG93u015767@Ubuntu>, relay=www-data@localhost
Jul 14 22:16:14 Ubuntu sm-mta[15776]: m6EKG9iC015776: from=<www-data@Ubuntu>, size=301, class=0, nrcpts=1, msgid=<200807142016.m6EKG93u015767@Ubuntu>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Jul 14 22:16:14 Ubuntu sendmail[15767]: m6EKG93u015767: to=mikeyinamsterdam@gmail.com, ctladdr=www-data (33/33), delay=00:00:05, xdelay=00:00:05, mailer=relay, pri=30092, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m6EKG9iC015776 Message accepted for delivery)
Jul 14 22:16:14 Ubuntu sendmail[15780]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:16:37 Ubuntu sendmail[15775]: unable to qualify my own domain name (Ubuntu) -- using short name
Jul 14 22:16:37 Ubuntu sendmail[15775]: m6EKGbgj015775: from=www-data, size=91, class=0, nrcpts=1, msgid=<200807142016.m6EKGbgj015775@Ubuntu>, relay=www-data@localhost
Jul 14 22:16:37 Ubuntu sm-mta[15782]: m6EKGbEw015782: from=<www-data@Ubuntu>, size=300, class=0, nrcpts=1, msgid=<200807142016.m6EKGbgj015775@Ubuntu>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Jul 14 22:16:37 Ubuntu sendmail[15775]: m6EKGbgj015775: to=mikeinamsterdam@gmail.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30091, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (m6EKGbEw015782 Message accepted for delivery)
Jul 14 22:16:37 Ubuntu sendmail[15786]: My unqualified host name (Ubuntu) unknown; sleeping for retry
Jul 14 22:16:39 Ubuntu sendmail[15747]: m6EKEdwK015747: from=www-data, size=95, class=0, nrcpts=1, msgid=<200807142014.m6EKEdwK015747@Ubuntu>, relay=www-data@localhost
Jul 14 22:16:39 Ubuntu sendmail[15747]: m6EKEdwK015747: to=mikeyinamsterdam@hushmail.com, delay=00:02:00, mailer=esmtp, pri=30095, dsn=4.4.3, stat=queued
Jul 14 22:17:03 Ubuntu sm-mta[15727]: m6EKBc8S015725: to=<michael562706@hotmail.com>, ctladdr=<www-data@Ubuntu> (33/33), delay=00:05:25, xdelay=00:05:25, mailer=esmtp, pri=120300, relay=mx1.hotmail.com. [65.54.245.8], dsn=4.0.0, stat=Deferred: mx1.hotmail.com.: No route to host[/COLOR][/I]

---

