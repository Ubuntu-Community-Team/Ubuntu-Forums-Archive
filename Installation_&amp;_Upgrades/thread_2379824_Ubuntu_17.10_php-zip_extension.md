---
title: "Ubuntu 17.10 php-zip extension"
date: 2017-12-10
forum: Installation &amp; Upgrades
---

### Post by robmro27 on 2017-12-10
Hello today I tried to install php-zip on my Ubuntu-17.10 but I have probems and can't resolve it.
```
php -v
PHP 7.1.12-1+ubuntu17.10.1+deb.sury.org+1 (cli) (built: Nov 29 2017 10:04:39) ( NTS )
Copyright (c) 1997-2017 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2017 Zend Technologies
    with Zend OPcache v7.1.12-1+ubuntu17.10.1+deb.sury.org+1, Copyright (c) 1999-2017, by Zend Technologies

```
After
```
sudo add-apt-repository ppa:ondrej/php

```
The command update returns something like that for that repository:
```
E: Repository 'http://ppa.launchpad.net/ondrej/php/ubuntu artful InRelease' changed its 'Label' value from '***** The main PPA for PHP (5.6, 7.0, 7.1) with many PECL extensions *****' to '***** The main PPA for supported PHP versions with many PECL extensions *****'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.


```

And I can't install php-zip
```
robert@robert-Inspiron-3543:~/projects$ sudo apt-get install php-zip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 php-zip : Depends: php7.1-zip but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
robert@robert-Inspiron-3543:~/projects$ sudo apt-get install php7.1-zip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 php7.1-zip : Depends: libzip5 (>= 1.0) but it is not installable
E: Unable to correct problems, you have held broken packages.
robert@robert-Inspiron-3543:~/projects$ sudo apt-get install libzip5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libzip5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'libzip5' has no installation candidate
robert@robert-Inspiron-3543:~/projects$ 

```

Thanks for help in advance.

---

### Post by robmro27 on 2017-12-10
Sorry for bothering you it worked if I use apt install instead apt-get, so
```
apt-get install php-zip
``` 
not works and 
```
apt install php-zip 
```
worked.

I'am unfortunately not sure why ? Maybe somebody could explain t to me.

---

