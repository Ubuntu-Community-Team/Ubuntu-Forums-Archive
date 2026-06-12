---
title: "Apache Folder gone"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by MasthaX on 2008-07-22
Hello i'm having this problem with Apache2 i messed up my 000-default file in sites-enabled so i thought i'd reinstall Apache. So i did.

```

sudo apt-get remove apache2
sudo apt-get install apache2

```

But when i checked it was using the same config files. So i removed Apache again and deleted the /etc/Apache2 folder

Then i reinstalled apache again through apt-get but there is no Apache2 folder in /etc/

When i check in my browser my site works but i can't edit any configs because the files are missing?

Can anyone tell me how to get them back or reinstall them?

Thanks in advance

Edit: after a reboot my Apache wouldn't start anymore (logic, since the config folder is deleted).

---

### Post by ibutho on 2008-07-22
Try the following
```
sudo apt-get purge apache2
```
and then reinstall apache2.

---

### Post by MasthaX on 2008-07-22
Yeah well Apache seems to be fine after that, but its not reading PHP pages anymore, i  tried reinstalling the php-apache lib but still no succes.

---

### Post by cpetercarter on 2008-07-22
The package needed is libapache2-mod-php5, which works with apache2-mpm-prefork. Is that the one you have re-installed?

---

### Post by MasthaX on 2008-07-23
Yes i searched on this forum and reinstalled that package without any luck.

Ok i have purged the php5 and libapache2-mod-php5 packages and reinstalled them everything is fine now, thank you for your support.

---

