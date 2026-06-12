---
title: "Postfix problems after upgrade"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by ReadAloud on 2005-10-26
Hi,

after a more or less smooth dist-upgrade to Breezy,  those of my mail accounts which use localhost as an smtp server stopped working. The offending lines in /etc/postfix/master.cf apparently were lines 80 and 81:

```

127.0.0.1:smtp inet n   -       -       -       -       smtpd
::1:smtp       inet n   -       -       -       -       smtpd

```

The problem was fixed by commenting them out and replacing them with:

```

smtp      inet  n       -       -       -       -       smtpd

```

Did anyone else experience this problem, and is there an explanation why a dist-upgrade would mess around with my postfix config?

---

### Post by DW5 on 2005-10-26
I have experienced a different problem with postfix that I would like to tag onto this thread.

I'm a linux end user living in a largely groupwise mail environment.  I'm doing some legwork trying to resolve a weird problem.  I use Mutt/Postfix from a linux laptop.  I send mail using postfix to my domain's smtp server.  It sends outside the domain perfectly.  However, when the mail gets routed to our domain's Groupwise system, my mail disappears.  I don't get undeliverable, or any other errors.  Any ideas why this might be happening and how I can resolve it (as in what do I need to do to my postfix setup to get it to work), or the direction I need to point my sysop in?

See my main.cf file below--with a touch of xfakeryx regarding the domain since this will post on the web and I don't want it perfectly easy to for spamcrawlers to mine.

Thanks,

DW  


# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

mydomain = xsnu.edux
myhostname = DUUbuntu.xsnu.edux
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = xsnu.edux, localhost.localdomain, localhost.localdomain, localhost
relayhost = [smtp.xsnu.edux]
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

---

