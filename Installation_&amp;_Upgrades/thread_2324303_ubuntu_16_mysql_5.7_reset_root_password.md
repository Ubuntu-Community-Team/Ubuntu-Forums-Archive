---
title: "ubuntu 16 mysql 5.7 reset root password"
date: 2016-05-12
forum: Installation &amp; Upgrades
---

### Post by cristiano9 on 2016-05-12
How could I reset root password of mysql 5.7 in Ubuntu 16.04 LTS??

dpkg-reconfigure mysql-server-5.7 DON'T WORK!

---

### Post by cristiano9 on 2016-05-16
none?!?!??!

---

### Post by QIII on 2016-05-16
Hello!

If you do not bump an unanswered thread at about 12 hours and instead leave it for three days, it will get buried and won't be noticed.

Further, a sarcastic bump will do little to attract assistance.  Just the word "bump" will do.

Cheers!

---

### Post by howefield on 2016-05-16
Feel free to give your post a daily bump if no response. Sometimes it is just a matter of catching someone with the answer at the right time.

In the absence of knowing whether or not you know the original password I'll direct you to the following link which is pretty comprehensive in how  to reset/change the mysql password.

[http://dev.mysql.com/doc/refman/5.7/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.7/en/resetting-permissions.html)

---

### Post by cristiano9 on 2016-05-17
don't have a easy command as [COLOR=#000000]dpkg-reconfigure mysql-server-5.7[/COLOR]??

---

### Post by cristiano9 on 2016-05-17
[COLOR=#000000]bump[/COLOR]

---

### Post by lisati on 2016-05-18
There is a procedure for resetting the password on the [MySql documentation page]("http://dev.mysql.com/doc/refman/5.7/en/resetting-permissions.html"). You will have to scroll down the page for the section that would be relevant for Ubuntu.

---

### Post by danthemango on 2016-05-30
I'm reading the documentation as lisati suggested, but I'm not sure about this part: > 1. Log on to your system as the Unix user that the MySQL server runs as (for example, mysql). Am I supposed to know what the password for that unix user is? I don't remember setting it up.

---

### Post by synkan on 2017-03-12
I found this on a forum and it helped me to reset my password under similar circumstances:

[http://rricketts.com/reset-root-password-mysql-5-7-ubuntu-16-04-lts/](http://rricketts.com/reset-root-password-mysql-5-7-ubuntu-16-04-lts/)

---

