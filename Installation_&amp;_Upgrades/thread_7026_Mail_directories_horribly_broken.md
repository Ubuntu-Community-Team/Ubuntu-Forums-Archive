---
title: "Mail directories horribly broken"
date: 2004-12-03
forum: Installation &amp; Upgrades
---

### Post by mdognrdog on 2004-12-03
I had gotten my mail-handling chain dialed in quite nicely under Gentoo (which I left for other reasons).  I had all my mail in maildirs in my ~ directory, delivered from my ISP's pop server by a perl script to the proper folders, and sent outgoing via ssmtp (Simple SMTP).  Perfect for a single-user laptop setup.  I don't need the capabilities of postfix, fetchmail, or procmail at all.  

Ubuntu is interfering quite radically with my ability to set things up the way I want, because of the permissions and mailbox locations that postfix (or something) seems to be demanding.  I need to be able to write to my mail directories, but I can't change the permissions on my own mail directories

For some reason, Ubuntu's mutt won't let me pick a mail directory other than /var/mail/mmd, and it won't honor my configuration variables telling it to check mail in my preferred folders in my ~ directory.  Also, to install ssmtp for my outgoing mail, I have to uninstall Postfix, AND ubuntu-base (and that sounds kind of scary).

Is there any way to just tell Postfix/Fetchmail/Procmail to just leave me alone without breaking EVERYTHING?   Or a guide on how to just have Postfix relay my mail to my ISP, and leave everything else alone?

---

### Post by wallijonn on 2004-12-05
Just for the heck of it,

Start a root terminal,
```

cd /etc
postfix stop
newaliases
postfix start
exit

```
{reboot}

---

