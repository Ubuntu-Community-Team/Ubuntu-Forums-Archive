---
title: "Cannot get phpmyadmin working"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by cepete02 on 2007-11-23
I have followed instructions to install phpmyadmin as follows:
sudo apt-get install mysql-server
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin

When I try to access the phpmyadmin home page using [http://localhost/phpmyadmin](http://localhost/phpmyadmin),  It tries to download a random .phtml file  (one example being "elogxewa.phtml"  if I try to access setup, using setup.php, it simply tries to download the file instead of opening it as a web page.

Any assistance would be greatly appreciated.

---

### Post by june_c21 on 2007-11-29
i'm having the same problem too.

anyone please help.

---

### Post by raxz on 2007-12-11
I am having the same problems as well. I already ran 
```

/etc/mysql/my.conf

```

and everythin is ok. I think this is a config problem....

---

### Post by dj_lightning on 2007-12-13
Try this...
```
sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
```

More on this here...
[http://ubuntuforums.org/showthread.php?t=591952](http://ubuntuforums.org/showthread.php?t=591952)

---

### Post by ruibernardo on 2007-12-13
Don't make links to phpmyadmin. Re[install LAMP with tasksel]("https://help.ubuntu.com/community/ApacheMySQLPHP") (purge if needed) and look at this thread: [phpmyadmin package does not install under /var/www]("http://ubuntuforums.org/showthread.php?p=3688994").

---

### Post by Liesmith Loki on 2008-02-28
I have the same problem, with the random phtml file. I've followed all the help in the links that have been posted. I had accidentally created a link to the phpmyadmin folder based on the advice, before reading that I should have just reconfigured phpmyadmin to configure apache2. So I deleted the link, and I reconfigured it. Still, [http://localhost/phpmyadmin](http://localhost/phpmyadmin) doesn't work, and it still asks me to download a random phtml file. I think this may have been because of the link, since before it would just tell me that it could not find the page. But I have already deleted the link. Is there some way the link still exists even though it doesn't show?

In addition, phpmyadmin STILL doesn't install into my /var/www folder. I really need help with this. Can anyone give it to me? I'm uninstalled and reinstalled LAMP dozens of times already, but to no avail.

---

