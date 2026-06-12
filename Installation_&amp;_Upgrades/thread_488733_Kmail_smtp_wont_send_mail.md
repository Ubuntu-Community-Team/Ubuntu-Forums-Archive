---
title: "Kmail smtp wont send mail"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by lwalsh on 2007-06-30
Hi folks

Not sure it it's the right forum, but I've searched this site and google high and low to no avail. I've got kubuntu 7.04 and evolution and thunderbird working fine so I know my settings but kmail will not send via smtp. I can get it to download, but not send. 

the error is 

Sending failed:
Internal Error
Please send a full bug report at [http://bugs.kde.org](http://bugs.kde.org)
Unhandled error condition. Please send a bug report.
The message will stay in the 'outbox' folder until you either fix the problem (e.g. a broken address) or remove the message from the 'outbox' folder.
The following transport protocol was used:
xxxx

xxxx is whatever text I put in the name field of the smtp settings

I've reinstalled kmail and deleted kmailrc from /home/liam/.kde/share/config to no avail. 

What's bugging me is I cannot see where I'm going wrong...

ps. anyone know how to point evolution to a differnet place to store mail (if kmail is no go, I'd like to point evolution to my existing thunderbird mail and use that instead.

thanks!

---

### Post by lwalsh on 2007-07-01
ok, I've fixed the problem with kmail - disabling the wallet enabled it to work fine.

---

