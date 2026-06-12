---
title: "How Do You Upgrade To PhpMyAdmin 3.4.5?"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by AlexanderDGreat on 2011-10-08
Hi,

I am hosting a simple web application with Ubuntu 10.04 LTS, and LAMP installed. After that I ran:

```
sudo apt-get install phpmyadmin
```

Now, I want to upgrade PHPMYADMIN to 3.4.5, it's the latest version as of now.

Can you recommend a good tutorial because I might mess up my installation, I haven't found a decent one online yet.

Thanks. :D :)

---

### Post by ubudog on 2011-10-08
Hey there - you can get the latest PhpMyAdmin by adding this PPA:
[https://launchpad.net/~nijel/+archive/phpmyadmin](https://launchpad.net/~nijel/+archive/phpmyadmin)

Enjoy!

---

### Post by ubudog on 2011-10-08
Thought I might give some more instructions.  After adding that PPA, run this to install the latest:
```
sudo apt-get update
```

then:

```
sudo apt-get install phpmyadmin
```

:)

---

### Post by AlexanderDGreat on 2011-10-09
Oh wow that easy! Thanks so much.

I've installed Ubuntu Tweak along so I can monitor my PPA's.

Thanks ubudog.

---

### Post by AlexanderDGreat on 2011-10-09
It worked!

I just needed to remember the ADMIN password to handle MySQL Databases and it asked me if I were to replace my config.php.inc - I said keep my configuration.

Thanks ubudog. :)

---

