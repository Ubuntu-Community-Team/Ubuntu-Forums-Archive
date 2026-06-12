---
title: "Can't get phpunit working"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by Vcize on 2011-07-25
Go easy on me here, as I'm fairly new to linux.  

We're developing in php with zend framework.

I installed phpunit using the installation instructions here: [http://www.phpunit.de/manual/current/en/installation.html](http://www.phpunit.de/manual/current/en/installation.html)

When I attempt to run phpunit I get the following error:

> PHP Warning:  require_once(PHPUnit/Util/Filter.php): failed to open stream: No such file or directory in /usr/bin/phpunit on line 46
PHP Fatal error:  require_once(): Failed opening required 'PHPUnit/Util/Filter.php' (include_path='/usr/bin:.:/usr/local/zend/share/ZendFramework/library:/usr/local/zend/share/pear/:/usr/share/php/PHPUnit/') in /usr/bin/phpunit on line 46

The Filter.php file is in /usr/share/php/PHPUnit

I figured it was most likely a path issue.  For whatever reason I have two php.ini files:
/usr/local/zend/share/dist/php.ini
/usr/local/zend/etc/php.ini

I'm not sure which one is actually used, so I've been editing both.

Here is my include path

> include_path = ".:/usr/local/zend/share/ZendFramework/library:/usr/local/zend/share/pear/:/usr/share/php/PHPUnit/"

Any ideas why it's not picking up that Filter.php file?  I've tried removing the trailing slashes from the include path as well.

---

### Post by Vcize on 2011-07-25
I think I've got it working now.  For anyone that stumbles across this in google, it turns out it was looking for the phpunit files in /usr/lib/php, which didn't exist (don't know why it ignores include_path).

So I just created a /usr/lib/php directory and put a symlink to the actual phpunit in there.



EDIT: Nevermind, it's not fixed after all.  I just got past that step because I was running phpunit from the /usr/lib/php directory (which causes other problems).  When I cd into another directory the same "failed to open PHPUnit/Util/Filter.php" pops up.

Yarg.

---

