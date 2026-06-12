---
title: "Relay issue Dovecot - Postfix"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by André_R on 2010-02-11
Hi,

I've got a box with postfix installed. I've added Dovecot to this. It seems to work ok, only when I sent a mail to a domain outside the servers own domains I receive a 
554 5.7.1 <...@hotmail.com>: Relay access denied 

Outlook has been configured with "verification on outgouging e-mail (SMTP)". Receiving Email is working ok.

I've been looking around, this seems to occur more often but I can't get this solved.

in postfix main.cf:
```
smtpd_sender_restrictions = permit_mynetworks, permit_sasl_authenticated
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions =  permit_mynetworks,
    permit_sasl_authenticated, reject_unauth_destination
broken_sasl_auth_clients = yes
```

in dovecot.conf:
```
auth default {
  mechanisms = plain login
  passdb pam {
  }
  userdb passwd {
  }
  socket listen {
    client {
      path = /var/spool/postfix/private/auth
      mode = 0660
      user = postfix
      group = postfix
    }
  }  
}
```

Does anybody know how to tackle this?

---

