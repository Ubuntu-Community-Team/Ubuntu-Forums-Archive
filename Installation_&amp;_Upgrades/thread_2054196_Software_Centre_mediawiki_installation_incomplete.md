---
title: "Software Centre mediawiki installation incomplete"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by jcoles on 2012-09-06
Has anyone been able to use MediaWiki as installed by the Ubuntu Software Centre? In my case, some files are missing and most file locations do not match the information in the MediaWiki wiki.

For example, LocalSettings.php and AdminSettings.php are not located in /. These essential files do not exist anywhere on my system.
In /var/lib/mediawiki there are broken links to these files which apparently should exist in /etc/mediawiki, which actually contains only apache.conf and cherokee.conf. 

I was asked to set a root password for MySQL, so I think that was installed. PHP perhaps was not. Firefox responds to a PHP URL by asking which application to use. Even setting execute permission on PHP files didn't change that.

Are there different instructions for Ubuntu? What's on the MediaWiki wiki doesn't match with what I can see on my machine. I can't use those instructions. Would it be better to ignore the Ubuntu packages and do the multiple and complex installation/configuration that the MediaWiki wiki describes?

---

### Post by jcoles on 2012-09-08
It is vital to understand that this mediawiki package just installs the web server, PHP, MySQL, and other required components. It does not actually install MediaWiki. 

You need to go to [www.mediawiki.org](www.mediawiki.org) and follow their instructions. In brief, this means:
[LIST]
[*]download the mediawiki tarball
[*]extract and copy the files to your web directory (usually /var/www/)
[*]access the index.php installation script through your browser.
[/LIST]
After all that, it's actually quite user-friendly.

---

