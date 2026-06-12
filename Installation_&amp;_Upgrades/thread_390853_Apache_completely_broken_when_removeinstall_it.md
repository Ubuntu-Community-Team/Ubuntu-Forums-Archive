---
title: "Apache completely broken when remove/install it"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by MockY on 2007-03-22
*empty*

---

### Post by MockY on 2007-03-22
I installed by mistake apache (1.3) instead of apache2. The webserver worked when first installed apache but php didn't. So I figured I would uninstall apachae and install apache2 instead. Said and done, I did but now it does not work.

I removed everything that has to do with Apache and installed apache2 from scratch again. It adds the www folder again and so forth, but localhost does not display the default page anymore. What am I doing wrong and what can I do to fix it?

Furthermore doing the following gives my no output. No errors or confiramtion:
```
sudo /etc/init.d/apache2 restart
```

If I do this instead, then it says that it stopped atleast, but anything else gives me nothing.
```
sudo /etc/init.d/apache2 stop
```

---

### Post by K.Mandla on 2007-03-22
(Merged double-post. ;) )

---

### Post by MockY on 2007-03-22
Have no idea why that happened....I kinda removed the first post now.

EDIT: When I install 1.3 again, it does work, even though PHP is broken. But I don't want to run apache 1.3

---

