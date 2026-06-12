---
title: "[SOLVED] Installed PHP5, but it does not work"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by TennTux on 2007-05-01
**General Description**
I'm attempting to get PHP working on my system. A simple test appears to not be working. I believe I have read all the relevent FAQ (Frequently Asked Questions) and help. I expect the problem is something I have done, however, I don't see the problem. Both normal html pages and C/C++ based CGI are returned correctly. I have attempted to include all the relevent info below. I have not shown all the tests I have performed but my test file frog.php also fails with no php tags present.

**System and Installed Software**
I have installed *Linux, Ubuntu 6.06 LTS (Dapper Drake) Desktop Edition* on a *Pentium IV with 1Gb Ram and 100 Gb hard disk*. I am using *firefox [1.5.dfsg+1.5.0.11-0ubuntu0.6.06.1]*, *Apache2 [2.0.55-4ubuntu2.1]*, *PHP [5.1.2-1ubuntu3.6]*, *libapache2-mod-php5 [5.1.2-1ubuntu3.6]*. Not relevent but I do have MySql installed. All packages where downloaded using Synaptic Package Manager and where prebuilt. In otherwords I did not build the softwrae. Also, I have not installed PHP4.

**Configuration**
*php5.load* and *php5.conf* are included in the *Apache2.conf* file and */usr/lib/apache2/modules/libphp5.so* exists. Also added *PHPINIDir /etc/php5/apache2* to *Apache2.conf*. Also tried it with *PHPINIDir /etc/php5/apache2/php.ini*

**Test Files**
*/var/www/testphpform.html* See attachement
*/usr/lib/cgi-bin/llama.php* See attachement
*/usr/lib/cgi-bin/frog.php* See attachement

**Log File / Error Message**
The last 2 lines of */var/log/apache2/error.log*
```
[Mon Apr 30 16:39:00 2007] [error] [client 127.0.0.1] (8)Exec format error: exec of '/usr/lib/cgi-bin/llama.php' failed, referer: http://localhost/testphpform.html
```
```
[Mon Apr 30 16:39:00 2007] [error] [client 127.0.0.1] Premature end of script headers: llama.php, referer: http://localhost/testphpform.html
```

---

### Post by obrient on 2007-05-01
I am still learning php, but I do know that an easy way to see if PHP is installed all you have to do is create a php file with the following line in it. 

[PHP]<?php phpinfo();?>[/PHP]

Then save it as something like index.php and place it in the /var/www/ directory. This will then list all of your PHP information.

I also know that a common thing that happens when I have run into the problems is always dealing with permissions. The default user for Apache in Ubuntu is **www-data** and I tend to make the group owner www-data. To see who owns the files and what group the file belongs to do an **ls -alh** which will list the files and permissions. Hope this helps some.

---

### Post by TennTux on 2007-05-01
Thanks for the suggestion. However, neither of my test pages work and one of them has no php tag in the page. So it must be a more fundamental problem. As for permissions I have set them to 755 (Owner: RWX; Group: RX; World: RX). I did put the php files in cgi-bin for a test since I was sure that CGI worked from that directory though I will try putting them directly in /var/www to see if that makes a difference.

---

### Post by TennTux on 2007-05-01
Found the problem.

The suggestion lead me in the correct direction.
My test php script files need to be in the root directory not a *ScriptAlias* directory. I suspect an Alias directory would also work.

Thanks for the help.

---

