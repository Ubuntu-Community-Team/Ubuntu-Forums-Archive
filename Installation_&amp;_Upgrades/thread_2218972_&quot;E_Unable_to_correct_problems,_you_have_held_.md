---
title: "&quot;E: Unable to correct problems, you have held broken packages&quot;"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by rompstar on 2014-04-22
Had major problems with this upgrade on one of my test servers, bottom line I can't install php5 for some stupid reason, I can't figure this out.

When I do a test page in apache for info.php, the page is blank, need help - wordpress all works via php5 and mysql, so my hobby site is all down right now :- )

I thought I could trust this upgrade, big mistake, won't be doing that in the future anymore :- )

<?php
phpinfo();
?>

Not sure how to get these depends fixed, I tried many thing... wasted hours :- ) so I am here now.

sudo apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 php5 : Depends: libapache2-mod-php5 (>= 5.5.11+dfsg-2+deb.sury.org~trusty+2~) but it is not going to be installed or
                 libapache2-mod-php5filter (>= 5.5.11+dfsg-2+deb.sury.org~trusty+2~) but it is not going to be installed or
                 php5-cgi (>= 5.5.11+dfsg-2+deb.sury.org~trusty+2~) but it is not going to be installed or
                 php5-fpm (>= 5.5.11+dfsg-2+deb.sury.org~trusty+2~) but it is not going to be installed
        Depends: php5-common (>= 5.5.11+dfsg-2+deb.sury.org~trusty+2~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
[email]raymond@dragonfly:/etc/apt/sources.list[/email].d$

---

### Post by rompstar on 2014-04-22
Just following up - I installed a ppa-purge and then purged a ppa, I think that was causing the problems and then it worked, I was able to install the php5 and other components, I got the idea from here:

[http://www.jamestitcumb.com/posts/downgrading-ondrejphp5-to-ondrejphp5-oldstable](http://www.jamestitcumb.com/posts/downgrading-ondrejphp5-to-ondrejphp5-oldstable)

---

