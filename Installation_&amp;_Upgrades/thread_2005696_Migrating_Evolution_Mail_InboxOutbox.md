---
title: "Migrating Evolution Mail Inbox/Outbox"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by Valkhorn on 2012-06-18
When I upgraded to Ubuntu 12.04, it completely hosed my Evolution client. The mbox was corrupted and I wasn't able to send any mail. All of my old emails were not retrievable. 

I found my old outbox and inbox (four years of mail, 500 megs each) and have backed them up and copied the files to my desktop. I would like to just copy these files to my new Evolution folder - but doing a search only pulls up:

```

[2]+  Stopped                 find / -name Inbox
wfarmer@wfarmer:~/.local/share/evolution/mail$ sudo find / -name Inbox
/usr/share/evolution/3.2/default/ko/mail/local/Inbox
/usr/share/evolution/3.2/default/ro/mail/local/Inbox
/usr/share/evolution/3.2/default/gu/mail/local/Inbox
/usr/share/evolution/3.2/default/sl/mail/local/Inbox
/usr/share/evolution/3.2/default/cy/mail/local/Inbox
/usr/share/evolution/3.2/default/gl/mail/local/Inbox
/usr/share/evolution/3.2/default/lt/mail/local/Inbox
/usr/share/evolution/3.2/default/zh_TW/mail/local/Inbox
/usr/share/evolution/3.2/default/it/mail/local/Inbox
/usr/share/evolution/3.2/default/pt_PT/mail/local/Inbox
/usr/share/evolution/3.2/default/sr@latin/mail/local/Inbox
/usr/share/evolution/3.2/default/nl/mail/local/Inbox
/usr/share/evolution/3.2/default/pt_BR/mail/local/Inbox
/usr/share/evolution/3.2/default/sr/mail/local/Inbox
/usr/share/evolution/3.2/default/id/mail/local/Inbox
/usr/share/evolution/3.2/default/cs/mail/local/Inbox
/usr/share/evolution/3.2/default/ru/mail/local/Inbox
/usr/share/evolution/3.2/default/ca/mail/local/Inbox
/usr/share/evolution/3.2/default/hu/mail/local/Inbox
/usr/share/evolution/3.2/default/es/mail/local/Inbox
/usr/share/evolution/3.2/default/mk/mail/local/Inbox
/usr/share/evolution/3.2/default/sv/mail/local/Inbox
/usr/share/evolution/3.2/default/nb/mail/local/Inbox
/usr/share/evolution/3.2/default/fr/mail/local/Inbox
/usr/share/evolution/3.2/default/ug/mail/local/Inbox
/usr/share/evolution/3.2/default/sk/mail/local/Inbox
/usr/share/evolution/3.2/default/ast/mail/local/Inbox
/usr/share/evolution/3.2/default/ja/mail/local/Inbox
/usr/share/evolution/3.2/default/C/mail/local/Inbox
/usr/share/evolution/3.2/default/hr/mail/local/Inbox
/usr/share/evolution/3.2/default/pt/mail/local/Inbox
/usr/share/evolution/3.2/default/pl/mail/local/Inbox
/usr/share/evolution/3.2/default/fi/mail/local/Inbox
/usr/share/evolution/3.2/default/zh_CN/mail/local/Inbox
/usr/share/evolution/3.2/default/bg/mail/local/Inbox
/usr/share/evolution/3.2/default/de/mail/local/Inbox
/usr/share/evolution/3.2/default/af/mail/local/Inbox
/usr/share/evolution/3.2/default/he/mail/local/Inbox
/home/wfarmer/.thunderbird/9mfm4271.default/Mail/www.metamedia.us/Inbox
/home/wfarmer/.local/share/evolution/mail/local/Inbox
/home/wfarmer/Desktop/Inbox

```

/Desktop/Inbox is where I backed it up
/home/wfarmer/.local/share/evolution/mail/local/Inbox is the old Inbox

So where would I copy this file to? I'm not able to do an import through evolution as it comes up with errors, so I'd rather just copy the file over and be done.

1) Is this possible? If so, how.
2) How else can I restore this Inbox through the command line?

Thanks!

---

