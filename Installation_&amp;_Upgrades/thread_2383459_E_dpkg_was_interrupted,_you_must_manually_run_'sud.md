---
title: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct"
date: 2018-01-25
forum: Installation &amp; Upgrades
---

### Post by Frank P on 2018-01-25
Ubuntu 16.04LTS running the most recent upgrade hung when reached MySQL. Can't get the exact error line because when I try to rerun the upgrade I get the error in subject line
Running sudo dkpg --configure -a hangs at 

Setting up mysql-server-5.7 (5.7.21-0ubuntu0.16.04.1) ...

This has happened several times in the past and I've had to eventually do a clean install. I'd rather not have to do it again.
I've tried everything I could find here, and by googling, but nothing works
Any other suggestions
Thanks
Frank

---

### Post by xptriado on 2018-01-27
> **Frank P said:**
> Ubuntu 16.04LTS running the most recent upgrade hung when reached MySQL. Can't get the exact error line because when I try to rerun the upgrade I get the error in subject line
Running sudo dkpg --configure -a hangs at 

Setting up mysql-server-5.7 (5.7.21-0ubuntu0.16.04.1) ...

This has happened several times in the past and I've had to eventually do a clean install. I'd rather not have to do it again.
I've tried everything I could find here, and by googling, but nothing works
Any other suggestions
Thanks
Frank

i'm having the same issue.

does anyone know what it could be?

stuck at :
```
Setting up mysql-server-5.7 (5.7.21-0ubuntu0.16.04.1) ...
```

---

### Post by kiskrof on 2018-09-24
I am having exactly the same issue too, when trying to install Calibre, Clementine and Amarok. The original post is from January 2018 and this is September 2018.... I installed my system yesterday (LTS 18.4) I could install Calibre a different way, going to the Calibre web page. I guess it works with other apps too. However, it would be cool to fix Ubuntu Software.

---

### Post by wildmanne39 on 2018-09-24
Old Thread Closed! If you need help please start your own thread, if you received this error:
> sudo dpkg --configure -a
Then running that command usually fixes the issue.

---

