---
title: "Install roundcube, ubuntu server"
date: 2019-08-05
forum: Installation &amp; Upgrades
---

### Post by fredy50 on 2019-08-05
Hello,

I'm trying to install mail server on my ubuntu server.

I'm comeing to step3 error create database into roundcube steps.

Error steps:
**Check DB config**

[COLOR=#000000][FONT=&amp]DSN (write):  [/FONT][/COLOR][COLOR=#FF0000 !important][FONT=&amp]**NOT OK**[/FONT][/COLOR][COLOR=#000000][FONT=&amp](SQLSTATE[HY000] [1045] Access denied for user 'roundcube'@'localhost' (using password: YES))[/FONT][/COLOR][COLOR=#666666][FONT=&amp]Make sure that the configured database exists and that the user has write privileges
DSN: mysql://roundcube:xxxxxxxxxxx@localhost/roundcubedb

---------------
i can log into phpmyadmin with the user. and it's set to localhost the user.

Can some one help me with this? Thanks:)[/FONT][/COLOR]

---

### Post by fredy50 on 2019-08-05
I removed the user in phpmyadmin and added new one.


I got new error:

IMAP connect:  NOT OK(Login  failed for [EMAIL="postmaster@hvass7.com"]postmaster@hvass7.com[/EMAIL] from 192.168.0.10. Wrong startup  greeting (localhost:143): * BYE Disconnected: Auth process broken)

---

### Post by fredy50 on 2019-08-05
i follow the guide here and it works for me :)

[https://workaround.org/ispmail/wheezy/connecting-postfix-to-the-database](https://workaround.org/ispmail/wheezy/connecting-postfix-to-the-database)

---

