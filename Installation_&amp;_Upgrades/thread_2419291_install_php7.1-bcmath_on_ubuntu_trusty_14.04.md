---
title: "install php7.1-bcmath on ubuntu trusty 14.04"
date: 2019-05-19
forum: Installation &amp; Upgrades
---

### Post by baudouin-laloy on 2019-05-19
This question is only for **Trusty (14.04).**.. Here is what I have done to install php7.1-bcmath:


```
    sudo add-apt-repository ppa:ondrej/php
    sudo apt update
    sudo apt install php7.1-bcmath

```

But I got the following result


```
    E: Unable to locate package php7.1-bcmath

```


I assume this is because **ppa:ondrej/php** support ubuntu versions starting from 16.04 and upper.


Is there a way to circumvent this? Like copying a deb file and using dpkg (If yes, where is this file)?


FYI, here is the result of `apt-cache search php7` (very small isn't it?)


```
    php7.1-cli - command-line interpreter for the PHP scripting language
    php7.1-readline - readline module for PHP
    php7.1-opcache - Zend OpCache module for PHP
    php7.1-mysql - MySQL module for PHP
    php7.1-zip - Zip module for PHP
    php7.1-mbstring - MBSTRING module for PHP
    php7.1-json - JSON module for PHP
    php7.1-xml - DOM, SimpleXML, WDDX, XML, and XSL module for PHP
    php7.1 - server-side, HTML-embedded scripting language (metapackage)
    php7.1-gd - GD module for PHP
    php7.1-curl - CURL module for PHP
    php7.1-bz2 - bzip2 module for PHP
    libapache2-mod-php7.1 - server-side, HTML-embedded scripting language (Apache 2 module)

```
I know that I should upgrade this system, but I am afraid to do it as if any problem I will have no time to fix it as I am going in vacation after tomorrow... (and this is a production system)

---

### Post by Xian on 2019-05-19
For further details regarding end-of-life for PHP on 14.04 you may want to read here:

[https://www.patreon.com/posts/ubuntu-14-04-php-22093917](https://www.patreon.com/posts/ubuntu-14-04-php-22093917)

Also see package author's comments about continued PHP installs on 14.04:
> The current state of packaging is archived in the git repository and if you want to shoot yourself into the foot, you can compile your own packages, it’s pretty simple to do so.

---

### Post by baudouin-laloy on 2019-05-20
Hi Xian,

I think you gave me the first step: I must compile it.
Do you know how to do so?

Thank you

---

