---
title: "PHPMyAdmin - Recurring error &amp; setup problems"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by mafitzpatrick on 2006-06-17
Hi All,

Trying to set up phpmyadmin on my system - everything else (apache/etc.) is in place and working properly. I downloaded the package through the manager and set it to install.  On starting I get the following error:

"The configuration file now needs a secret passphrase (blowfish_secret). "

I have since re-installed the package, and after checking the phpmyadmin website run the config utility. The suggestion seems to be to edit the settings in the config.inc.php file to include the line $cfg['blowfish_secret'] = 'somethingsecret'; and to copy this also to the blowfish_secret.inc.php file.

I've done this - in 2 places:  In /etc/phpmyadmin (both files) and also in /var/www/phpmyadmin (which has completely different config files). None of this has achieved very much, so.... any ideas?!

Thanks,

---

### Post by burgermann on 2006-06-22
It's most likely that the apache linuxuser hasn't got read permission to the /etc/phpmyadmin/blowfish_secret.inc.php. Maybe you have changed the group which apache uses?

---

### Post by mafitzpatrick on 2006-06-22
Thanks for the suggestion burgermann but that's (almost!) definately not the case. I haven't changed the apache user and wouldn't know how to in fact.

The rights for that file are currently:

user: root  (rwx)
group: www-data (r)

Assuming that the www-data group is apaches, it should be able to read it?

Thanks for your help! Any more suggestions?

---

### Post by mafitzpatrick on 2006-06-22
I just tried setting the file perms to readable by all & it worked.  Bizarrely it continues to work after I've set them back.  At a bit of a loss here, but at least it seems to be doing it right now.

---

