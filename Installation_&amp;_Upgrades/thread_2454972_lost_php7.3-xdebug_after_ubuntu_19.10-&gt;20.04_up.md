---
title: "lost php7.3-xdebug after ubuntu 19.10-&gt;20.04 upgrade"
date: 2020-12-09
forum: Installation &amp; Upgrades
---

### Post by kmchen2 on 2020-12-09
I had php7.3 runing on Ubuntu 19.10, then after upgrade to 20.04 I see php7.4 was installed and websites built on php7.3-fpm still work but not xdebug

I found xdebug.ini in /etc/php/7.3/fpm/mods-available  renamed to xdebug.ini.dpkg-bak.

Manually restablishing the conf:
```

~# ll /etc/php/7.3/mods-available/xdebug.ini
-rw-r--r-- 1 root root 204 déc.  10 00:15 /etc/php/7.3/mods-available/xdebug.ini
~# ll /etc/php/7.3/fpm/conf.d/20-xdebug.ini 
lrwxrwxrwx 1 root root 38 déc.  10 00:12 /etc/php/7.3/fpm/conf.d/20-xdebug.ini -> /etc/php/7.3/mods-available/xdebug.ini
~# systemctl reload php7.3-fpm
~# cat /etc/php/7.3/fpm/conf.d/20-xdebug.ini
zend_extension=xdebug.so
#zend_extension=xdebug.so
xdebug.remote_enable=1
xdebug.remote_handler=dbgp
xdebug.remote_mode=req
xdebug.remote_port=9000

```
I get that error in php7.3-fpm.log:
```

PHP message: PHP Warning:  Failed loading Zend extension 'xdebug.so' (tried: /usr/lib/php/20180731/xdebug.so (/usr/lib/php/20180731/xdebug.so: cannot open shared object file: No such file or directory)

```
20180731/xdebug.so no longer exists and has been replaced:
```

# locate xdebug.so
/usr/lib/php/20190902/xdebug.so

```

php-xdebug is installed but what about php7.3-xdebug ?
```


~# dpkg -l *xdebug*
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom            Version                   Architecture Description
+++-==============-=========================-============-=====================================
ii  php-xdebug     2.9.2+2.8.1+2.5.5-1build1 amd64        Xdebug Module for PHP
un  php7.4-xdebug  <aucune>                  <aucune>     (aucune description n'est disponible)


```

I got to work tomorrow on a project. Any help apreciated

---

### Post by kmchen2 on 2020-12-10
After reinstall, following [https://pixelspress.com/how-to-install-php-7-3-fpm-on-ubuntu-19-10/](https://pixelspress.com/how-to-install-php-7-3-fpm-on-ubuntu-19-10/)  (20.04 version not found), error message changes:

```

# systemctl reload php7.3-fpm
...
Failed loading /usr/lib/php/20190902/xdebug.so:  /usr/lib/php/20190902/xdebug.so: undefined symbol: zend_get_properties_for

```

---

### Post by kmchen2 on 2020-12-10
Is that the best Ubuntu forum ? I come from Debian, testing Ubuntu and don't know a lot about that distrib support. Are there more active forums ?

---

### Post by kmchen2 on 2020-12-15
No it is not. I found on stack overflow that 20180731 php7.3 should be used with php7.3 and now xdebug seems to work but is it normal that parameters seem have changed when I kept the same php version ? 

Following instructions page [https://xdebug.org/docs/upgrade_guide#changed-%22xdebug.remote_host%22](https://xdebug.org/docs/upgrade_guide#changed-%22xdebug.remote_host%22) I ended with that for localhost debuging on port 9003 (seems that port default value can't be changed now):
```
# cat /etc/php/7.3/fpm/conf.d/20-xdebug.ini 
zend_extension=/usr/lib/php/20180731/xdebug.so
xdebug.mode=debug
xdebug.start_with_request=trigger

```
Now it works

---

