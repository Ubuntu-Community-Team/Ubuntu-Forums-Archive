---
title: "Upgrade from 13.04 to 13.10 broke apache and maybe more"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by networkguy09 on 2014-04-08
Hello, I apologize for my noobness. I upgraded my server from 13.04 to 13.10 as a way to patch this openssl vulnerability.

When I attempt to start apache up I get the following

```
service apache2 start
 * Starting web server apache2                                                                                                                                           *
 * The apache2 configtest failed.
Output of config test was:
AH00526: Syntax error on line 86 of /etc/apache2/apache2.conf:
Invalid command 'LockFile', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
```

I also noticed the apache2.conf file is now readonly. I don't believe it was that way prior to the upgrade. I also think mysql is broke (or needs to be configured again). I won't really know until I get the web server working though. My mail server is working. So the upgrade didn't break everything. Any help is appreciated.

---

### Post by Ubi_one_2014 on 2014-04-08
that lockfile problem can be solved by:
[http://askubuntu.com/questions/368515/upgraded-to-ubuntu-13-10-apache-not-able-to-start](http://askubuntu.com/questions/368515/upgraded-to-ubuntu-13-10-apache-not-able-to-start)

---

### Post by networkguy09 on 2014-04-09
Thanks... I did see that page but was unable to edit the file since it's read only. I'm guessing I need to chmod the file... I'm just not sure what the permissions were on it before the upgrade.

---

### Post by networkguy09 on 2014-04-09
Okay, went ahead and chmod the file to be able to edit it and chmod back the way it was when I was done.

Now this...

```
service apache2 start
 * Starting web server apache2                                                         *
 * The apache2 configtest failed.
Output of config test was:
AH00526: Syntax error on line 46 of /etc/apache2/sites-enabled/default-ssl.conf:
SSLCertificateKeyFile: file '/etc/ssl/private/myserver.key' does not exist or is       empty
Action 'configtest' failed.
The Apache error log may have more information.


```

Guessing the certificate was lost during the upgrade... Speaking of I was planning to regenerate all my ssl keys anyways (for mail, jabber server, https, ssh). How may I do that?

---

### Post by Ubi_one_2014 on 2014-04-09
googling on your error brings me to:
[https://www.digitalocean.com/community/articles/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-12-04)

---

### Post by networkguy09 on 2014-04-09
Hello,
I just happen to try starting apache as the root user and that worked. I don't understand why because I had previously added my regular user account to this file using sudo visudo. It's still there after the upgrade.

```
 useraccount ALL=(ALL:ALL) ALL 
```

It seems like the upgrade just changed a bunch of file permissions and my normal useraccount cannot access the directory, therefore, can't launch apache. I can't even begin to think of how I could go about verifying all of my files and directories to figure out what changed and why. Hopefully someone can shed some light on that!

I had to actually su to the root account which is something I'd like to avoid. It's my understanding you should sudo everything when possible.

---

### Post by networkguy09 on 2014-04-09
The upgrade itself was done using the root user account through a type of "console" connect to the server. I didn't think a remote upgrade via SSH was a good idea.

---

