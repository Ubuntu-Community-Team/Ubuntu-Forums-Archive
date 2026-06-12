---
title: "Dovecot POP3 authentication"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Michael R on 2008-04-30
I'm feeling pretty stuck, I have setup ubuntu with LAMP using postfix and dovecot for the mail services. I can't get the pop3 server to authenticate me in my mail.log during dovecot startup I noticed I get 

[Apr 30 20:28:11 Pserver dovecot: Dovecot v1.0.5 starting up
Apr 30 20:28:11 Pserver dovecot: auth(default): APOP mechanism can't be supported with given passdbs
Apr 30 20:28:11 Pserver dovecot: Auth process died too early - shutting down
Apr 30 20:28:11 Pserver dovecot: child 5604 (auth) returned error 89
]

I used the guide at [http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/) to help get me going as I am pretty new to linux.
my dovecot.conf files segment that has auth default looks like this
auth default {
  mechanisms = plain login
  passdb passwd {
  }
  userdb passwd {
  }
socket listen {
client {
path =/var/spool/postfix/private/auth
mode = 0660
user = postfix
group = postfix
}
}
}

I understand that it isn't seeing a password file to authenticate users against? first, am I right? second.. I'm kinda lost on how to fix it. a little nudge in the right direction should help me get it going

thanks everyone
Mike

---

