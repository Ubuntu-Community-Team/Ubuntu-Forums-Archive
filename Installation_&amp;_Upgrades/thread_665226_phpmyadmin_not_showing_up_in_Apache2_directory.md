---
title: "phpmyadmin not showing up in Apache2 directory"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by VolvoPunch on 2008-01-12
My Problem, I am running the desktop version  of xubuntu 7.10 I think.

```
systemadmin@atlbricks:/var/www$ sudo apt-get install phpmyadmin
[sudo] password for systemadmin:
Reading package lists... Done
Building dependency tree
Reading state information... Done
phpmyadmin is already the newest version.
The following packages were automatically installed and are no longer required:
  libpcap0.7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
systemadmin@atlbricks:/var/www$ phpmyadmin
-bash: phpmyadmin: command not found
systemadmin@atlbricks:/var/www$ ls
apache2-default
systemadmin@atlbricks:/var/www$

```

---

### Post by MobiusNZ on 2008-01-12
Xubuntu should be able to have phpmyadmin fine... I have it on my Kubuntu desktop machine for local dev...
Have you played with any of the files in /etc/apache2 ?

---

### Post by dabang on 2008-01-12
During installation of phpmyadmin you should be asked for which web server it's supposed to be configured. If you answered "apache2" there, you should be able to navigate to it by
[http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin)

If that doesn't work, go to your apache's document root directory (I think /var/www per default) and create a symlink to phpmyadmin

```
cd /var/www
sudo ln -s /usr/share/phpmyadmin/
```

Now the above should work.

---

### Post by VolvoPunch on 2008-01-13
> **dabang said:**
> During installation of phpmyadmin you should be asked for which web server it's supposed to be configured. If you answered "apache2" there, you should be able to navigate to it by
[http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin)

If that doesn't work, go to your apache's document root directory (I think /var/www per default) and create a symlink to phpmyadmin

```
cd /var/www
sudo ln -s /usr/share/phpmyadmin/
```

Now the above should work.

Thanks making the link worked :), I still don't know why there was not a link there in the first place and why I get the command not found error when I type phpmyadmin. Still no problem because its working now :guitar:

---

### Post by dabang on 2008-01-19
By default phpmyadmin is configured during package installation by altering apache's configuration (at least with gutsy) - unless you didn't pick a server type, so the link should not have been necessary. But it's work around and I used it myself with other distros.
> why I get the command not found error when I type phpmyadmin
"phpmyadmin" is no executable, it's a suite of php scripts which need a web server to work.

---

