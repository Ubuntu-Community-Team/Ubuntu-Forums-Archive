---
title: "Sendmail and Postfix help to a relay"
date: 2018-06-10
forum: Installation &amp; Upgrades
---

### Post by bdf0506 on 2018-06-10
I am attempting to configure "mail" and postfix.

I am using an Ubuntu 18.04 server
I am using a Synology Diskstation as a mail relay. I know that this relay is configured correctly, as other servers can talk to it and send mail via it.

But, I'm at a loss for the proper way to configure postfix to send mail to it. Am i configured properly as shown below?

main.cf looks like this:

```
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destinationmyhostname = nagios.home
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = nagios.home, localhost.home, localhost
relayhost = diskstation.home
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = all
```


Once the mail gets to the Synology server, it has issues with it, and seems to try to send one email to my desired recipient (which never arrives), and then another from the synology system back to the server, which fails.

Any ideas?

---

### Post by bdf0506 on 2018-06-11
[FONT=Monaco, Andale Mono, Courier New, Courier, monospace][COLOR=#666666]Figured this out. Answer here: [/COLOR][/FONT]https://forum.synology.com/enu/viewtopic.php?f=238&t=143192&p=531726#p531726

---

