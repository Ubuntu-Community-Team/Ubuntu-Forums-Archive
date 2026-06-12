---
title: "Where is LAMP's &quot;www&quot; folder on Ubuntu 9.10?"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by AccesInterzis on 2010-02-18
I`ve installed LAMP on ubuntu 9.10. Apache works. phpmyadmin works. Everything is great. But I can't get to "www" folder. Before I was running windows on my PC and for web development i was using easyphp and then it was pretty easy. I was making 2-3 clicks and I was getting in "www" folder of easyphp where i could do everything: create folders, files, download my wp blog from the server hosting and so on. No , how can I do all these on ubuntu? Because i tried to download my wp blog in "www" through filezilla and the system didn't let me to do anything in "www" folder of LAMP.

I recently installed ubuntu on my PC. It is the first time when i run an OS other than windows and i feel like a child who is learnig to walk. I got the old habits from windows and it is quite hard to work on ubuntu. But i am willing to learn ubuntu because i don't want to use cracked software anymore. At least as much as i can.

---

### Post by lewisforlife on 2010-02-18
Should be /var/www

If you do not have permission to put files in /var/www it means that a different user owns the folder than you are using.  You can do a 

```
sudo chown [user] /var/www
```

to change the user of /var/www.

---

### Post by AccesInterzis on 2010-02-19
I did what you taught me but it doesn't let me to open the root folder from File Browser. It tells I do not have permissions.

---

### Post by stlsaint on 2010-02-19
in terminal on system with apache run:
```
chown -R www-data:www-data /var/www/
```

---

### Post by AccesInterzis on 2010-02-19
I fixed it. It works now. Thanks a lot.

---

