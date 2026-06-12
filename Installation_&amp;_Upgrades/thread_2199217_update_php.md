---
title: "update php"
date: 2014-01-12
forum: Installation &amp; Upgrades
---

### Post by Joe67 on 2014-01-12
hi, i am a newbie runing unbuntu 12.04lts on a vps, am looking for help how to update php to latest  release.. at the moment its Version of [PHP]("http://www.php.net/"):     [B]5.3.10-1ubuntu3.6

cheers
[/B]

---

### Post by sandyd on 2014-01-13
If you really do need to update, see this ppa -> [https://launchpad.net/~ondrej/+archive/php5](https://launchpad.net/~ondrej/+archive/php5), however, I reccomend that you stay with the current release unless there is a depdency issue, or an application that really needs php 5.5

---

### Post by Joe67 on 2014-01-16
thanks for the reply, i seen it mentioned on another for were other nuke users were upgrading. just trying to look into it more, see if its worth it.

i was told

> PHP5  offers reduced consumption of memory, increased security against  exploitation of vulnerabilities in PHP scripts and its easier  programming through new functions and extensions that have been added.  
 
Most host I have found have upgraded their PHP version that the sites  they host without notifying them. By not upgrading,  you are just going  to force people running more secured sites to either have a bunch of  errors show up, (unless they turn off error reporting), or force them to  use a older system which still uses old coding that has been  depreciated for new and better coding.                                                       


---

### Post by SeijiSensei on 2014-01-16
That appears to be talking about differences between versions 4 and 5 of PHP, not about differences among versions of PHP5 itself.  Like sandyd, I suggest you stick with the repository version unless there is some feature not available in 5.3.

Recent security fixes, if any, will be "backported" to the release version, so you need not worry about that issue either.

---

