---
title: "Installing Sendmail - No configuration?"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by musse1 on 2007-01-04
I have installed Sendmail but it won't send any mails:p Am I not supposed to configure it or anything and add my smtp server? What could be wrong? I just installed it and added the path in my php.ini file.

---

### Post by musse1 on 2007-01-04
This is the errors:
  GNU nano 1.3.12           File: /var/log/mail.log

Jan  4 15:21:01 server sm-msp-queue[4568]: unable to qualify my own domain name$
Jan  4 15:40:01 server sm-msp-queue[4597]: My unqualified host name (server) un$
Jan  4 15:41:01 server sm-msp-queue[4597]: unable to qualify my own domain name$
Jan  4 15:45:57 server sm-mta[3676]: My unqualified host name (server) unknown;$
Jan  4 15:45:57 server sm-msp-queue[3698]: My unqualified host name (server) un$
Jan  4 15:46:57 server sm-mta[3676]: unable to qualify my own domain name (serv$
Jan  4 15:46:57 server sm-mta[3676]: gethostbyaddr(192.168.0.161) failed: 1
Jan  4 15:46:57 server sm-msp-queue[3698]: unable to qualify my own domain name$
Jan  4 15:46:58 server sm-mta[3712]: starting daemon (8.13.8): SMTP+queueing@00$
Jan  4 15:47:07 server sendmail[3780]: My unqualified host name (server) unknow$
Jan  4 15:48:07 server sendmail[3780]: unable to qualify my own domain name (se$
Jan  4 15:48:07 server sendmail[3780]: l04Em7Mf003780: from=www-data, size=330,$
Jan  4 15:50:41 server sendmail[3783]: My unqualified host name (server) unknow$
Jan  4 15:51:41 server sendmail[3783]: unable to qualify my own domain name (se$
Jan  4 15:51:41 server sendmail[3783]: l04Epfbf003783: from=www-data, size=326,$
Jan  4 16:00:01 server sm-msp-queue[3871]: My unqualified host name (server) un$
Jan  4 16:01:01 server sm-msp-queue[3871]: unable to qualify my own domain name$

---

### Post by musse1 on 2007-01-04
all I want is to send emails using smtp. How do i do that? I can't find any good guide for this or anything that is for help. I already have LAMP installed.

---

### Post by thor918 on 2007-02-13
I can't help say exactly whats wrong with your config.
but I too have a LAMP server and struggeled to get it working.

what worked for me was:
apt-get install postfix

and then edit php.ini
Relevant lines in /etc/php5/apache2/php.ini:

[mail function]
; For Win32 only.
SMTP = localhost
smtp_port = 25

; For Win32 only.
;sendmail_from = [email]me@example.com[/email]

; For Unix only. You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = /usr/sbin/sendmail -t -i


and edited /etc/postfix/main.cf and put my correct external smtp server
relayhost = smtpauth.earthlink.net

restart the services that had configuration changes

---

### Post by dcstar on 2007-02-13
> **musse1 said:**
> all I want is to send emails using smtp. How do i do that? I can't find any good guide for this or anything that is for help. I already have LAMP installed.

Installing the **postfix** package was all I needed, if you have a correct host name for your system then it should work (not "localhost"!!!)

The only thing I needed to do was "tweak" one config file to send e-mails with a real domain name, so those other SMTP servers that do a DNS validity check will accept my outgoing mail.

---

### Post by etola on 2007-02-23
> **dcstar said:**
> Installing the **postfix** package was all I needed, if you have a correct host name for your system then it should work (not "localhost"!!!)

The only thing I needed to do was "tweak" one config file to send e-mails with a real domain name, so those other SMTP servers that do a DNS validity check will accept my outgoing mail.

How did you tweaked your config ?

Another thing is, when I'm at work I enter the domain name of that domain but when I connect at home, the work domain does not work naturally. But in that case, what should I enter for the hostname ? do you have any idea?

---

