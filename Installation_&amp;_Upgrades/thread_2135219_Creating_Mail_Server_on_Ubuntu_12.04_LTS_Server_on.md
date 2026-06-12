---
title: "Creating Mail Server on Ubuntu 12.04 LTS Server on a VPS"
date: 2013-04-13
forum: Installation &amp; Upgrades
---

### Post by lucknuts on 2013-04-13
I've worked with ubuntu linux several times. I'm still a beginner for the most part I'd say. Long story short, I'm having difficulties creating a mailserver on my VPS.

I have server.domain.com as my VPS address.
I have domain [www.domain.com]("http://www.domain.com") as my website.
I need to create a MX record that points to mail.domain.com > which I assume will point to my VPS...

I have WEBMIN installed. I was able to install dovecot and that is working fine?

This is the dovecot imap test
```

root@connect:~# telnet localhost imap
Trying ::1...
Connected to localhost.localdomain.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN] Dovecot ready.

```

This is the dovecot pop3 test
```

root@connect:~# telnet localhost pop3
Trying ::1...
Connected to localhost.localdomain.
Escape character is '^]'.
+OK Dovecot ready.
```

I have Sendmail and Postfix installed. I've tried multiple documentation and I'm still unable to get a mailserver to work. From within webmin I can send mail out no problem. I'm unable to receive any mail to any of the users.

Please help!

This is installing a mailserver on a VPS.

---

### Post by darkod on 2013-04-13
If I'm not mistaken, the postfix main.cf file has an option for mynetworks or similar. You need to tell it it can receive main from all public IPs. Did you do that?

To be able to receive mail directly from any mailserver in the world you would have to allow 0.0.0.0/0 I think. Save and close the file. Restart postfix.

Also, from another machine when you do ping mail.domain.com does it show your server public IP? Did you make the mail A record in the registrar control panel where the domain is? You need to create it as A host, just putting mail doesn't mean anything. In fact, you can call it as you wish, people usually call it mail.

PS. Also try
telnet mail.domain.com 25

to see if postfix will respond. If it doesn't, the DNS is probably not configured right. No one can send you email if your DNS is not correctly configured or the mail server doesn't respond.

Why did you install both sendmail and postfix, don't they clash? I'm not a mail expert myself, so I'm only asking. You only need one MTA which is postfix. And one MDA to allow pop3/imap connections, which is dovecot. Nothing else.

---

### Post by lucknuts on 2013-04-14
You're definitely right, it looks like once I installed courier it began working. I had sendmail uninstaled and used postfix, which wasn't working...

I now have dovecot working with the above stats. I have sendmail working also...

```
root@connect:~# telnet mail.domain.com 25
Trying 7.9.19.159...
Connected to mail.domain.com.
Escape character is '^]'.
220 connect.domain.com ESMTP Sendmail 8.14.4/8.14.4/Debian-2ubuntu2; Mon, 15 Apr 2013 01:07:17 +0400; (No UCE/UBE) logging access from: connect.domain.com(OK)-connect.domain.com [7.9.19.159]
```

So, all in all I'm able to use dovecot and sendmail.

I'm able to send/receive emails from within webmin. So far that's it...

Tried installing roundcube, kept coming up with a ton of error, might give another shot at a few things...

---

