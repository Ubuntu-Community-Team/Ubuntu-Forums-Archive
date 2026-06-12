---
title: "Ubuntu 10.4 Breaks PHP5"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by cryptodan on 2010-05-03
I just upgraded to the latest version of Ubuntu 10.4, and now none of my PHP Scripted pages are working.  Instead they are being downloaded, and not executed via apache.  I have set all the options in Apache to use libphp5.so, yet the pages fail to display.  Instead I am now prompted to download the file.

How can I get this fixed?

---

### Post by brydonhunter on 2010-05-03
Usually this could indicate that your apache server is either not started or php was not installed.

Check it out.

---

### Post by cryptodan on 2010-05-04
Actually it was an issue with my Firefox Browser.  I had to completely clear my browsing history to enable it to be displayed.

---

### Post by Wim Sturkenboom on 2010-05-04
Thanks. That's very interesting. At occasion I experience this issue with Firefox where pages from the web (e.g on ubuntuforums or linuxquestions) are indeed behaving like this. A little later, it's OK again (and I don't clean the history).

When I indeed opt to save, the file is empty.

[COLOR="Blue"]*Question would be why this is happening?*[/COLOR] My feeling still is that it's a serverside or network issue but I might be wrong there.

Anybody any thoughts?

---

### Post by cryptodan on 2010-05-04
It only happened after upgrading to 10.04.  Its weird.

---

### Post by tgalati4 on 2010-05-04
Cache management is a black art.  You would have to get into the firefox source code to see what triggers cache clearing.

It can certainly throw you when you are modifying pages and your test browser is not behaving because you haven't cleared your cache.

You can use private browsing and that clears your cache rather effectively.

---

### Post by SteveWh on 2010-05-04
Did 10.04 come with a new version of Apache? New version of PHP?

The behavior you described can be related to the MIME type returned in the page headers, when a .html page has PHP code in it and Apache has been configured to parse .html files as .php. The .htaccess (or httpd.conf) lines to accomplish that (parse .html as .php) differ depending on the server's configuration, mainly Apache version but maybe PHP version and other factors, as well.

All the methods of doing it are something of a workaround. One of the methods can result in the page being sent to the browser with a MIME type that the browser doesn't recognize as an HTML page, so it doesn't display it by default, and offers to download it.

Sorry to be so vague, but the factors are complicated enough that the solution is usually to get a list of the various ways of getting .html pages parsed as if they were .php pages, and then use trial and error until one works for you. 

Hope this might lead in the direction of a solution. A web search that might be useful is:
Apache parse html as php

---

### Post by GuardStar on 2010-05-09
Well I had a similar thing happen after my last update on my server i use for web development. After the update (which updated apache) I got the same problem when trying to load my site.

I use webmin to administrate the server so i checked the Apache Modules and noticed that the php5 module was unchecked. When I tried to active it I was told it couldn't find the php5-mod.so. I had to re-install libapache2-mod-php5 to get it to work again.

I then discovered that my MySQL code wasn't working and had to re-install php5-mysql to fix that.

Not sure what in the Apache update would cause those modules to uninstall??

---

### Post by quonsar on 2010-05-19
Very strange - I installed last night, and my site either returns a blank page, OR does something VERY strange: with no prompt to download occuring, the page will display but the url changes by itself from, for example, [http://www.mydomain.com/myphpscript.html](http://www.mydomain.com/myphpscript.html) to file:///tmp/myphpscript-1.tmp. It didn't occur to me it might be a firefox issue. I'll fool with it some more when I get home.

---

### Post by GinKen on 2010-05-25
Maybe this thread is too old, but I'm having the same problem described here, and I'm wondering if anyone else here who has had the same problem has found a solution.  If so, please enlighten.  Since upgrading, I can't open any php files at [http://localhost](http://localhost) in browser (Firefox).   However, opening .html files works fine.
Thanks

---

### Post by SteveWh on 2010-05-26
> **GinKen said:**
> I can't open any php files at [http://localhost](http://localhost) 
When you try to open the php files, what happens instead of the page loading normally? Do you get the download prompt?

Note that in previous replies a few things to check have been mentioned. For example, check in Synaptic Package Manager to see that the PHP5 module is still installed, and maybe check other related modules, too.

---

### Post by GinKen on 2010-05-27
Thanks for reply.  Sorry didn't notice it for awhile as went to new page.  
PHP5 is installed.  Also
"~$ sudo a2enmod php5
Module php5 already enabled "
What happens when I try to open a php file is .. nothing.  No warnings, just a blank page.  Keep in mind, I'm just using apache to view my own php pages I'm writing.  Before upgrading to 10.4 from karmic I could view them fine.

---

### Post by dtrot55 on 2010-06-26
Does anyone know of a good resource to learn how to use php in ubuntu?  I googled for awhile but didn't find anything that kind of walked you through the whole here is how to install apache...mysql and php...any help would be much appreciated

---

### Post by SteveWh on 2010-06-27
I'm using my Jaunty installation as a reference, not Lucid, but this should get you started in the right direction.

In Synaptic Package Manager, install these and any dependencies they need:

apache2
apache2-doc (or was it apache2.doc?)
apache2.2-common
php5
php5-mysql
php-doc
phpmyadmin
mysql-client
mysql-server
mysql-admin
mysql-doc-5.0 (or most recent version available)
mysql-query-browser

You might eventually want or need a bunch more related packages, but that's the basic core, I think.

apache2 and php5, I believe, install hassle-free into a default configuration.

mysql might ask you to set up a "root" (main, master, with global privileges) MySQL user account and associated password. 

phpmyadmin will, I think, ask you to set up a "control user" account and password. The "control user" is counter-intuitively actually a very low-privileged account that you only use for some phpmyadmin tasks. The phpmyadmin install might be the most confusing part of the installation, but I can't remember exactly what it asked me to do. If it's confusing, do the best you can; you can redo it later if necessary. phpMyAdmin is just one of the possible ways to communicate with your MySQL server. You might not end up using it much. I prefer the MySQL command line, or the Query Browser.

Once Apache2 is installed, you can browse to http: // localhost / doc (remove spaces), which gives you an interface to the generally very good documentation for Apache2 (apache2-doc), PHP (php-doc/), and MySQL (mysql-server/, then follow link to "refman"). 

The MySQL documentation has a short tutorial / command line walkthrough that is very helpful for getting oriented to what MySQL is all about.

-----

As I recall, the default Apache2 + PHP5 installation is sufficient to let you start creating your experimental .php pages without any additional tinkering or configuration, though it's likely you'll need to do some of that later. 

Using MySQL from within PHP5 is going to be complex. Learn how to use MySQL from the command line first.  

-----

Apache2, PHP, and MySQL are very big "areas of knowledge", so if it seems like there's an awful lot to learn and get accustomed to, it's because there is, not just all of them together but each of them individually. I've been studying and practicing MySQL basically all day every day for the past 5 weeks, and am starting to feel reasonably confident with it.  That is, it can take a while.

Where to start will depend on your interests and goals. If it's PHP/MySQL, look at the easier and newer MySQL connection methods called "mysqli" rather than the older and less good "mysql" methods.

---

### Post by malialipali on 2011-11-27
Same problems here. I upgraded 7.04 all the way to 8.10 and now to 10.4.

After upgrading to 10.4, php (along with wiki 1.12) started producing errors like:

> PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/snmp.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/snmp.so' - /usr/lib/php5/20090626+lfs/snmp.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  require(./index.php): failed to open stream: No such file or directory in /var/www/wiki/index.php5 on line 1
PHP Fatal error:  require(): Failed opening required './index.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/wiki/index.php5 on line 1

So I change the snmp.ini, just to humor the old server, and now I get this...


> php /var/www/wiki/index.php
PHP Warning:  require_once(./StartProfiler.php): failed to open stream: No such file or directory in /var/www/wiki/includes/WebStart.php on line 69
PHP Fatal error:  require_once(): Failed opening required './StartProfiler.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/wiki/includes/WebStart.php on line 69


or if started from that directory:
> 
HP Parse error:  syntax error, unexpected T_NAMESPACE, expecting T_STRING in /var/www/wiki/includes/Namespace.php on line 49
PHP Notice:  Undefined index: SERVER_PROTOCOL in /var/www/wiki/includes/OutputHandler.php on line 112

And wiki pages turn just plain blank page.
Now.... I tried reinstalling and purging php5, but to no effect. 
I would really really hate to reinstall  the server as it is running non-stop since 2007. There are also a number of nice ages tucked in mysql for that wiki, and downgrading to my previous backup seems so non-kosher also.

By the way, Apache2 also won't accept server side inclusions, despite my attempts to enable it.
:confused:

---

### Post by cryptodan on 2011-11-27
Seems to me like you should consult the developer for Wiki 1.12 and ask him what to do.  Your issues are pointing towards software that has no support for the new PHP API.

---

### Post by malialipali on 2011-12-04
@cryptodan

I will install new version of MediaWiki (1.18), and then get back with results.

---

