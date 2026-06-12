---
title: "Upgrading PHP"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by cromerhigh on 2007-07-11
Hi,

I am completely new to using Ubuntu, I come from a Windows background. I have just purchased a dedicated server and it has Ubuntu 6.06 LTS installed.

I made a file phpinfo and then went to the PHP web site. Found a newer version of PHP was out 5.2.3 and wish to upgrade to this version.

The questions I have are:

1. How do I upgrade or can I upgrade to this PHP version?
2. Will I lose any settings or mods installed?

Remember I don't have a GUI installed so its in BASH Shell (i think its called that), and the only thing I have tried so far is apt-get php ...... and it does not update the PHP version I have to the newest one.

:popcorn:

Thanks,

Philip Smith.

---

### Post by az on 2007-07-11
Php5.2.1 is the version that is supported in Dapper.  That means that all the bog fixes and security vulnerabilities that are available are brought to Dapper.

If this is a production server and you don't really need any cutting edge features that are only available in 5.2.3, then stick with the version in Dapper.  It is safer to run slightly older software since it has a tendency to be better audited.

If you really need a feature that is only found in later versions, you can either dist-upgrade to Feisty (5.2.1) or wait for Gutsy to be release - currently, Gutsy has 5.2.3.

It is not recommended to compile php5 from source - you will lose all the benefits of the package manager and will not easily be able to keep up-to-date.

---

### Post by pspcz on 2007-07-30
is there a proper way to back off to php 5.1.6 from 5.2.1?

we are having issues between 5.2.1 and Zend optimizer 3.3, if we drop back zend to a previos version it is not compatible with 5.2.1 so we are going to trying to back up to an earlier version of php

this is on a new install, the same software is running on 5.1.6 with zend and no problem, however, on OS X servers


Pz

---

### Post by djjelly on 2007-09-03
> **az said:**
> Php5.2.1 is the version that is supported in Dapper.  That means that all the bog fixes and security vulnerabilities that are available are brought to Dapper.


Could you please tell me where I can find the version 5.2.1 for Dapper Drake ? Because I am in a situation where I have a dedicated server that is fully managed and they won't upgrade PHP under warranty unless I give them a Dapper Drake repository with the 5.2.* version of PHP.

At the moment my server is running PHP 5.1.2 (cli) and that is the same version I found in the dapper drake repository : [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=PHP5&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=PHP5&searchon=names&subword=1&version=dapper&release=all)

Please if you know where I can find a repository with PHP 5.2.* for Dapper Drake let me know. I need to start running Zend Framework that has v5.2 as min requirement. :(

Thank you.

---

### Post by az on 2007-09-04
Sorry, That was an error on my part.  5.2.1 is in Feisty (the current stable, but not LTS).

I don't know of a Dapper repo that has php5.2

---

### Post by djjelly on 2007-09-04
:( Sad !
And I thought there was a chance to upgrade damn PHP ...

Thanks for the reply ;)

Does anyone know if at least there are plans on adding a new version of PHP in the Dapper repository ? or where I can find out / ask someone ?

Thank you.

---

### Post by cg` on 2007-11-09
I'm also interested to see if there is a repository with PHP 5.1.3 or greater for Dapper.

Cheers :)

---

