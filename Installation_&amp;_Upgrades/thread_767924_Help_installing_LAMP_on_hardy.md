---
title: "Help installing LAMP on hardy"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by allspiritseve on 2008-04-26
Hello all,

Ever since edgy I've had problem-free installs of LAMP on my laptop... however, I just made a fresh install of hardy, and things aren't going well. Everything installed just fine, but I can't run my php apps and localhost/phpmyadmin/ doesn't work. 

I get this error if I try and restart apache:
```
spirit2@spirit-laptop:~$ apache2 -k restart
apache2: bad user name ${APACHE_RUN_USER}

```

I have not found anything useful on this "bad user name" error. I don't understand why this doesn't work, its the same way I've installed it every other time. 

Any ideas? 

Thanks,

Cory

Edit: Never mind, I found a fix: [http://howtoforge.com/forums/showthread.php?p=108459](http://howtoforge.com/forums/showthread.php?p=108459)

---

