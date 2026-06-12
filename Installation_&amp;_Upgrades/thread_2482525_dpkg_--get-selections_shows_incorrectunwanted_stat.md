---
title: "dpkg --get-selections shows incorrect/unwanted state"
date: 2023-01-02
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2023-01-02
Running Ubuntu 20.04.5 LTS and am trying to figure out why 
```
dpkg --get-selections
```

shows packages that are needed if I want to go from php 7.4 to 8.1 with a state of 'deinstall'. If I read the doc correct, that means that these modules will be removed at some stage, which I definitely don't want as I need them (i.e. every module currently in 7.4 should also be installed in 8.1)

Full output is 

```
llist@mail1:~$ dpkg --get-selections | grep -i php
libapache2-mod-php				install
libapache2-mod-php7.2				install
libapache2-mod-php7.4				install
libapache2-mod-php8.0				install
libapache2-mod-php8.1				install
libapache2-mod-php8.2				install
php						install
php-bz2						install
php-cli						install
php-common					install
php-curl					install
php-gd						install
php-gmp						install
php-igbinary					install
php-imagick					install
php-intl					install
php-json					install
php-mbstring					install
php-mysql					install
php-pear					install
php-redis					install
php-xml						install
php-zip						install
php5.6-cli					install
php5.6-common					install
php5.6-igbinary					install
php5.6-imagick					deinstall
php5.6-json					install
php5.6-opcache					install
php5.6-phpdbg					install
php5.6-readline					install
php5.6-redis					deinstall
php7.0-cli					install
php7.0-common					install
php7.0-igbinary					install
php7.0-imagick					deinstall
php7.0-json					install
php7.0-opcache					install
php7.0-phpdbg					install
php7.0-readline					install
php7.0-redis					deinstall
php7.1-cli					install
php7.1-common					install
php7.1-igbinary					install
php7.1-imagick					deinstall
php7.1-json					install
php7.1-opcache					install
php7.1-phpdbg					install
php7.1-readline					install
php7.1-redis					deinstall
php7.2-bz2					deinstall
php7.2-cli					install
php7.2-common					install
php7.2-curl					deinstall
php7.2-gd					deinstall
php7.2-gmp					deinstall
php7.2-igbinary					install
php7.2-imagick					deinstall
php7.2-intl					install
php7.2-json					install
php7.2-mbstring					deinstall
php7.2-mysql					install
php7.2-opcache					install
php7.2-readline					install
php7.2-redis					deinstall
php7.2-xml					install
php7.2-zip					deinstall
php7.3-cli					install
php7.3-common					install
php7.3-igbinary					install
php7.3-imagick					deinstall
php7.3-json					install
php7.3-opcache					install
php7.3-phpdbg					install
php7.3-readline					install
php7.3-redis					deinstall
php7.4						install
php7.4-bcmath					install
php7.4-bz2					install
php7.4-cli					install
php7.4-common					install
php7.4-curl					install
php7.4-gd					install
php7.4-gmp					install
php7.4-igbinary					install
php7.4-imagick					install
php7.4-intl					install
php7.4-json					install
php7.4-mbstring					install
php7.4-mysql					install
php7.4-opcache					install
php7.4-readline					install
php7.4-redis					install
php7.4-xml					install
php7.4-zip					install
php8.0-bz2					deinstall
php8.0-cli					install
php8.0-common					install
php8.0-curl					install
php8.0-dev					install
php8.0-fpm					install
php8.0-gd					install
php8.0-gmp					install
php8.0-igbinary					install
php8.0-imagick					deinstall
php8.0-imap					install
php8.0-intl					install
php8.0-mbstring					install
php8.0-mysql					install
php8.0-opcache					install
php8.0-readline					install
php8.0-redis					deinstall
php8.0-soap					install
php8.0-xml					install
php8.0-xmlrpc					install
php8.0-zip					install
php8.1						install
php8.1-bcmath					install
php8.1-bz2					deinstall
php8.1-cli					install
php8.1-common					install
php8.1-curl					deinstall
php8.1-gd					deinstall
php8.1-gmp					deinstall
php8.1-igbinary					install
php8.1-imagick					deinstall
php8.1-intl					deinstall
php8.1-mbstring					deinstall
php8.1-mysql					deinstall
php8.1-opcache					install
php8.1-readline					install
php8.1-redis					deinstall
php8.1-xml					install
php8.1-zip					deinstall
php8.2						install
php8.2-bz2					install
php8.2-cli					install
php8.2-common					install
php8.2-curl					install
php8.2-gd					install
php8.2-gmp					install
php8.2-igbinary					install
php8.2-imagick					install
php8.2-intl					install
php8.2-mbstring					install
php8.2-mysql					install
php8.2-opcache					install
php8.2-phpdbg					install
php8.2-readline					install
php8.2-redis					install
php8.2-xml					install
php8.2-zip					install
pkg-php-tools					install

```

Not sure how this ended like this, but appreciate any fix

---

### Post by deadflowr on 2023-01-03
deinstall listings have already been removed.
The output is because of leftover configuration files from the packages stlll exist on the system.
There should be a direct match if you run
```
dpkg -l | grep ^rc
```
to the packages listed as deinstalled.
Packages that are rc'd are no longer installed on the system but old configs still remain.
This is a byproduct of apt's remove command, versus apt's purge command which would have remove all.

From man apt about remove and purge:
> Removing a package removes all packaged data, but leaves usually small (modified) user configuration files behind, in case the remove was an accident.
           Just issuing an installation request for the accidentally removed package will restore its function as before in that case. On the other hand you can get
           rid of these leftovers by calling purge even on already removed packages. Note that this does not affect any data or configuration stored in your home
           directory.


---

### Post by lister171254 on 2023-01-03
Thanks for the quick reply. 

I didn't remove/purge any php packages (manually), but this was a flow on of the issue I reported [https://ubuntuforums.org/showthread.php?t=2482103]("https://ubuntuforums.org/showthread.php?t=2482103")

```
llist@mail1:~$ dpkg -l | grep ^rc | grep php
rc  php5.6-imagick                         3.4.4+php8.0+3.4.4-7+ubuntu20.04.1+deb.sury.org+1                    amd64        Provides a wrapper to the ImageMagick library
rc  php5.6-redis                           5.3.4+4.3.0-1+ubuntu20.04.1+deb.sury.org+1                           amd64        PHP extension for interfacing with Redis
rc  php7.0-imagick                         3.4.4+php8.0+3.4.4-7+ubuntu20.04.1+deb.sury.org+1                    amd64        Provides a wrapper to the ImageMagick library
rc  php7.0-redis                           5.3.4+4.3.0-1+ubuntu20.04.1+deb.sury.org+1                           amd64        PHP extension for interfacing with Redis
rc  php7.1-imagick                         3.4.4+php8.0+3.4.4-7+ubuntu20.04.1+deb.sury.org+1                    amd64        Provides a wrapper to the ImageMagick library
rc  php7.1-redis                           5.3.4+4.3.0-1+ubuntu20.04.1+deb.sury.org+1                           amd64        PHP extension for interfacing with Redis
rc  php7.2-bz2                             7.2.33-1+ubuntu18.04.1+deb.sury.org+1                                amd64        bzip2 module for PHP
rc  php7.2-curl                            7.2.33-1+ubuntu18.04.1+deb.sury.org+1                                amd64        CURL module for PHP
rc  php7.2-gd                              7.2.33-1+ubuntu18.04.1+deb.sury.org+1                                amd64        GD module for PHP
rc  php7.2-gmp                             7.2.33-1+ubuntu18.04.1+deb.sury.org+1                                amd64        GMP module for PHP
rc  php7.2-imagick                         3.4.4+php8.0+3.4.4-7+ubuntu20.04.1+deb.sury.org+1                    amd64        Provides a wrapper to the ImageMagick library
rc  php7.2-mbstring                        7.2.33-1+ubuntu18.04.1+deb.sury.org+1                                amd64        MBSTRING module for PHP
rc  php7.2-redis                           5.3.4+4.3.0-1+ubuntu20.04.1+deb.sury.org+1                           amd64        PHP extension for interfacing with Redis
rc  php7.2-zip                             7.2.33-1+ubuntu18.04.1+deb.sury.org+1                                amd64        Zip module for PHP
rc  php7.3-imagick                         3.4.4+php8.0+3.4.4-7+ubuntu20.04.1+deb.sury.org+1                    amd64        Provides a wrapper to the ImageMagick library
rc  php7.3-redis                           5.3.4+4.3.0-1+ubuntu20.04.1+deb.sury.org+1                           amd64        PHP extension for interfacing with Redis
rc  php8.0-bz2                             8.0.14-1+ubuntu20.04.1+deb.sury.org+1                                amd64        bzip2 module for PHP
rc  php8.0-imagick                         3.5.1-2+ubuntu20.04.1+deb.sury.org+3                                 amd64        Provides a wrapper to the ImageMagick library
rc  php8.0-redis                           5.3.4+4.3.0-5+ubuntu20.04.1+deb.sury.org+3                           amd64        PHP extension for interfacing with Redis
rc  php8.1-bz2                             8.1.13-1+ubuntu20.04.1+deb.sury.org+1                                amd64        bzip2 module for PHP
rc  php8.1-curl                            8.1.13-1+ubuntu20.04.1+deb.sury.org+1                                amd64        CURL module for PHP
rc  php8.1-gd                              8.1.13-1+ubuntu20.04.1+deb.sury.org+1                                amd64        GD module for PHP
rc  php8.1-gmp                             8.1.13-1+ubuntu20.04.1+deb.sury.org+1                                amd64        GMP module for PHP
rc  php8.1-imagick                         3.7.0-3+ubuntu20.04.1+deb.sury.org+1                                 amd64        Provides a wrapper to the ImageMagick library
rc  php8.1-intl                            8.1.13-1+ubuntu20.04.1+deb.sury.org+1                                amd64        Internationalisation module for PHP
rc  php8.1-mbstring                        8.1.13-1+ubuntu20.04.1+deb.sury.org+1                                amd64        MBSTRING module for PHP
rc  php8.1-mysql                           8.1.13-1+ubuntu20.04.1+deb.sury.org+1                                amd64        MySQL module for PHP
rc  php8.1-redis                           5.3.7+4.3.0-2+ubuntu20.04.1+deb.sury.org+1                           amd64        PHP extension for interfacing with Redis
rc  php8.1-zip                             8.1.13-1+ubuntu20.04.1+deb.sury.org+1                                amd64        Zip module for PHP

```

---

### Post by deadflowr on 2023-01-03
Packages removed don't necessarily have to be removed using the apt remove command.
Package updates can force a package removal if the update requires it.
And the autoremove command will remove packages that are [s]no longer useful or deemed useful[/s] considered obsolete by the system.

---

### Post by lister171254 on 2023-01-03
I reinstalled the required modules and now everything is as expectd.
Thanks for your help
```
php8.1						install
php8.1-bcmath					install
php8.1-bz2					install
php8.1-cli					install
php8.1-common					install
php8.1-curl					install
php8.1-dev					install
php8.1-gd					install
php8.1-gmp					install
php8.1-igbinary					install
php8.1-imagick					install
php8.1-imap					install
php8.1-intl					install
php8.1-mbstring					install
php8.1-mysql					install
php8.1-opcache					install
php8.1-readline					install
php8.1-redis					install
php8.1-soap					install
php8.1-xml					install
php8.1-xmlrpc					install
php8.1-zip					install
php8.2						install
php8.2-bz2					install
php8.2-cli					install
php8.2-common					install
php8.2-curl					install
php8.2-gd					install
php8.2-gmp					install
php8.2-igbinary					install
php8.2-imagick					install
php8.2-intl					install
php8.2-mbstring					install
php8.2-mysql					install
php8.2-opcache					install
php8.2-phpdbg					install
php8.2-readline					install
php8.2-redis					install
php8.2-xml					install
php8.2-zip					install
pkg-php-tools					install

```

---

