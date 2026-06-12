---
title: "installing latest mediawiki from source"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-05-28
i downloaded latest mediawiki, moved the tarball to /usr/share/  exploded the tarball via 

```
sudo tar -xf /usr/share/mediawiki[tab key to load rest of tarball string]
```

then

```

sudo ln -s /usr/share/mediawiki[tab to load version number]  /var/www/wiki

```

then in your web browser point to local host 127.0.0.1/wiki

it will then bring you to the wiki configuration setup pages, and you may install databases for this package via phpmyadmin.  im going to remove the alias to php my admin after i am done using it again to cut off outside world from seeing the php my admin login page for security reasons.

im going to do this by adding a # infront of the alias in /etc/apache2/conf.d/phpmyadmin.conf and making it look like this

```

# phpMyAdmin default Apache configuration

#Alias /phpmyadmin /usr/share/phpmyadmin

```

my next to default ubuntu install says we should install caching, and pecl.

pecl search in synaptic shows dh-make-php as first result.  install that, then install [http://pecl.php.net/package/intl](http://pecl.php.net/package/intl) extension for mediawiki. i already have apache mysql and php installed, but if you dont have those installed they are requried.

download latest [http://pecl.php.net/package/intl](http://pecl.php.net/package/intl) source, tar -xf intl* to explode package.

./autogen.sh yeilds /opt/php5 does not exist message

##  im clearly going to have to refine this....  php-apc shows up in synaptic, installing it does not stop the wiki installer page from throwing errors.  going to try [http://download.icu-project.org/files/icu4c/4.8/icu4c-4_8-src.tgz](http://download.icu-project.org/files/icu4c/4.8/icu4c-4_8-src.tgz) to see if that resolves one

download the latest source of eaccelerator.
[http://bart.eaccelerator.net/source/](http://bart.eaccelerator.net/source/)

tar -xf eaccelerator source package to explode it,

phpize command tells me i need php-dev package, i pull the package from synaptic.  i also grab libicu-dev while i am at it.

```
phpize
```

 goes through, then

```
./configure --prefix=/usr && make && sudo make install
```

```
sudo gedit /etc/php5/apache2/php.ini
```

add to the top of the file the e accelerator info.

```
[PHP]

; eAccelerator configuration
; Note that eAccelerator may also be installed as a PHP extension or as a zend_extension
; If you are using a thread safe build of PHP you must use
; zend_extension_ts instead of zend_extension
;extension                       = "/usr/lib/php5/20060613+lfs/eaccelerator.so"
zend_extension                  = "/usr/lib/php5/20060613+lfs/eaccelerator.so"
eaccelerator.shm_size           = "16"
eaccelerator.cache_dir          = "/var/cache/eaccelerator"
eaccelerator.enable             = "1"
eaccelerator.optimizer          = "1"
eaccelerator.check_mtime        = "1"
eaccelerator.debug              = "0"
eaccelerator.filter             = ""
eaccelerator.shm_max            = "0"
eaccelerator.shm_ttl            = "0"
eaccelerator.shm_prune_period   = "0"
eaccelerator.shm_only           = "0"
eaccelerator.compress           = "1"
eaccelerator.compress_level     = "9"
eaccelerator.allowed_admin_path = "/var/www/eaccelerator"

```


```
sudo mkdir -p /var/cache/eaccelerator
sudo chmod 0777 /var/cache/eaccelerator

```


```
sudo /etc/init.d/apache2 restart
```


[http://developer.mindtouch.com/en/kb/Improve_PHP_performance_with_eAccelerator_on_Ubuntu_8.04_%28Debian%29](http://developer.mindtouch.com/en/kb/Improve_PHP_performance_with_eAccelerator_on_Ubuntu_8.04_%28Debian%29)

then purge eaccelerator source directory and pure the tarball out of your system.

at this point we are going to make a database for the mediawiki by uncommenting the alias that keeps phpmyadmin shut off from attacks.

```

sudo gedit /etc/apache2/conf.d/phpmyadmin.conf
```

then

```
sudo /etc/init.d/apache2 restart
```

then point the browser @ 127.0.0.1/phpmyadmin

then setup your database for wikipedia, i named mine wiki

make a user, i named mine wiki.

password your database, and follow prompts in the media wiki package

comment the alias of phpmyadmin to disable the phpmyadmin pannel/address

restart apache and your good to go on linking the wiki.

---

### Post by boblizar on 2011-05-28
fixing the warnings for the backends isnt seeming to work as of right now, ill have to give it a break and come back to fixing them.  i know as of right now i could just blast right past them but im choosing to fix the warnings.

---

