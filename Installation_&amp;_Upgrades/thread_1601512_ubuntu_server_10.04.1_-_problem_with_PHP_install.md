---
title: "ubuntu server 10.04.1 - problem with PHP install"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by sbinkerd1 on 2010-10-20
Hello. I had downgraded my php install to what came before 5.3.2 because it didn't work with my joomla sites at the time. I just updated alot of packages including apache, but did not update the PHP to 5.3.2 yet. after all the packages went through now I have a broken php install:

here is the version I show on my system:

 dpkg -l| grep php
rc  libapache2-mod-php5                  5.2.10.dfsg.1-2ubuntu6                          server-side, HTML-embedded scripting languag
hi  php5-common                          5.2.10.dfsg.1-2ubuntu6                          Common files for packages built from the php
ii  php5-dev                             5.2.10.dfsg.1-2ubuntu6                          Files for PHP5 module development
rc  php5-gd                              5.2.10.dfsg.1-2ubuntu6                          GD module for php5
rc  php5-mcrypt                          5.2.6-0ubuntu2                                  MCrypt module for php5
rc  php5-mysql                           5.2.10.dfsg.1-2ubuntu6                          MySQL module for php5
rc  phpmyadmin                           4:3.3.2-1                                       MySQL web administration tool


I have these linked to the Karmic Repositories using the prescribed method below. this did work well until the last Apache upgrade I did.

[URL="http://www.nickveenhof.be/blog/reverting-or-downgrading-php-53-52-ubuntu-lucid-lynx-1004"]

now I get broken package errors:

> apt-get install php5-imap
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-imap: Depends: phpapi-20090626+lfs
E: Broken packages


The following packages have unmet dependencies:
  php5: Depends: libapache2-mod-php5 (>= 5.2.10.dfsg.1-2ubuntu6) but it is not going to be installed or
                 libapache2-mod-php5filter (>= 5.2.10.dfsg.1-2ubuntu6) but it is not going to be installed or
                 php5-cgi (>= 5.2.10.dfsg.1-2ubuntu6) but it is not going to be installed
E: Broken packages


ANY help is much appreciated!

---

### Post by sbinkerd1 on 2010-10-20
[Found a thread that matches this issue here]("http://ubuntuforums.org/showthread.php?t=1459163&highlight=php+unmet+dependencies&page=4")

---

