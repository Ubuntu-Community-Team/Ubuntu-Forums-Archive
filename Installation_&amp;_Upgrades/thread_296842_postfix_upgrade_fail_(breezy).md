---
title: "postfix upgrade fail (breezy)"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by cmattogno on 2006-11-10
[SIZE="2"]I tried to dist-upgrade on my server and recv'd this error:[/SIZE]

[SIZE="1"][FONT="Fixedsys"]Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
postalias: fatal: open database /etc/aliases.db: Permission denied
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/SIZE]

[SIZE="2"][FONT="Palatino Linotype"]Yes, I did "**sudo** apt-get upgrade". The perms on the file are 644 mail:mail. Luckily I had just backed up, so I was able to cp the aliases.db file and get postfix running. But whenever I run any apt-get install or upgrades I get the error again, and have to cp the aliases.db file and start postfix.

How do I fix this issue?

Thank you.

'topher[/FONT][/SIZE]

---

