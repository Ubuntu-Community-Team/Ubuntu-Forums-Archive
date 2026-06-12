---
title: "[SOLVED] squirrelmail not in /var/www/"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by yanny on 2008-02-02
Hi, 

I've installed squirrelmail via apt-get install squirrelmail.

root@ubuntu:/var/www# find / -name squirrelmail

/var/lib/squirrelmail
/var/spool/squirrelmail
/etc/cron.daily/squirrelmail
/etc/squirrelmail
/usr/share/squirrelmail
/usr/share/lintian/overrides/squirrelmail
/usr/share/doc/squirrelmail


It doesn't exists in /var/www therefore I cannot browse to it, could you tell me how I can make that a link or path to /var/www/squirrelmail?

---

### Post by BennBuntu on 2008-02-02
hmm, not sure which one of those you have to link to.
But open nautilus with root privileges.
```
gksudo nautilus /
```
then right click on squirrelmail, make link
then move that link to your /var/www/ and rename it to "squirrelmail" instead of "link to squirrelmail"

can use same method to link directories. I don't know if this is "the right way" but it's handy sometimes. :)

---

### Post by yanny on 2008-02-02
Thank you so much this is really helpful!! Thanks!! Now I can use this way to move other directories as well.

---

