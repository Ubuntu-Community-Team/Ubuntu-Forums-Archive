---
title: "postfix help"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by michie86 on 2007-03-01
I'm creating a web application using php and I want to add email functionality in it. I read this article in the community but I have some questions..

In the configuration part, 

Run:

dpkg-reconfigure postfix

Insert the following details when asked (replacing server1.example.com with your domain name if you have one):

    *

      Internet Site
    *

      NONE
    *

      server1.example.com
    *

      server1.example.com, localhost.example.com, localhost
    *

      No
    *

      127.0.0.0/8
    *

      Yes
    *

      0
    *

      +
    *

      all



my question is, what should I do with the 

 server1.example.com
 server1.example.com, localhost.example.com, localhost

?? If I only want my application to send email? And it's still not hosted? And I'm only using an ordinary computer running ubuntu6.06?


Thank you.

Hoping for your help,
michie

---

### Post by seppe on 2007-03-02
If you want to use dpkg-reconfigure, just setup up postfix as a **Satellite System** ad set a blank value for SMTP relay host.

Alternatively put this configuration in the file [FONT="monospace"]/etc/postfix/main.cf[/FONT].
Personalize the *myhostname* value and check that the file [FONT="monospace"]/etc/mailname[/FONT] contains your fully qualified domain name.
```
myhostname = server.example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, localhost.$mydomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
inet_protocols = ipv4
```
Remember to reload Postfix configuration executing:
[INDENT][FONT="monospace"]sudo invoke-rc.d postfix reload[/FONT][/INDENT]

---

### Post by michie86 on 2007-03-02
oops.. sorry but I didn't get any of that.. I'm doomed

what should I replace server1.example.com with? any example?
I'm using xampp for linux in my web application..

Thanks

---

### Post by scxtt on 2007-03-02
if you just want your box to be able to send mail (i use postfix so i can "mailx" myself config files) i don't think you have to get too elaborate (my hostname in this example is "kubuntu" - which is how 127.0.0.1 is defined in /etc/hosts):
```
[font=courier]myhostname = kubuntu
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = kubuntu, localhost.localdomain, , localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all[/font]
```

---

