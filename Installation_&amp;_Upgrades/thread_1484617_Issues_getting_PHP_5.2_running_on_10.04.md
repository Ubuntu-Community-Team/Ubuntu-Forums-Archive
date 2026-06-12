---
title: "Issues getting PHP 5.2 running on 10.04"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by TZRick on 2010-05-15
Hi everyone,

I just upgraded my production web server (which hasn't gone live yet...and is really an amateur effort) to 10.04 LTS.  I immediately ran into issues:

1. CiviCRM is not compatible with PHP 5.3.2 which is shipped with Ubuntu 10.04.

2. I tried uninstalling PHP 5.3 and installing PHP 5.2 using the script at [http://mrkandy.wordpress.com/2010/04/16/install-php-5-2-x-in-ubuntu-10-04-lucid/]("http://mrkandy.wordpress.com/2010/04/16/install-php-5-2-x-in-ubuntu-10-04-lucid/").  Now, when I try to bring-up a PHP page, I am asked to download the page.  I think libapache2-mod-php5 is missing, but I cannot figure out how to install only the PHP 5.2 version.

3. After running the script in #2 above, PHPMyAdmin no longer seems to work.  I uninstalled it and then tried reinstalling it, but the reinstall failed:

phpmyadmin: Depends: php5-mcrypt but it is not installable

So, I think the problem can be solved by:
1. Installing libapache2-mod-php5
2. Installing PHPMyAdmin from the last version of Ubuntu

Any ideas?

Thanks in advance!

---

### Post by attilahooper on 2010-06-18
I'm working on the same issues. Any results ?

I also tried this
[http://randyfay.com/node/63](http://randyfay.com/node/63)
No joy

---

