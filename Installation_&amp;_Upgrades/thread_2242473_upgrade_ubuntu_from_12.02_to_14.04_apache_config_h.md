---
title: "upgrade ubuntu from 12.02 to 14.04 apache config help"
date: 2014-09-02
forum: Installation &amp; Upgrades
---

### Post by btodd012 on 2014-09-02
During the upgrade to 14.04 I specified keeping my config. I have the web server up and running but my configs aren't updated yet.

I tried finding the default apahe2.conf (and all other default config files)  on apaches web sit and google searches. No luck so far. I'm not sure how to safely get them from the apache package without overwriting exisiting files.

I also found documentation in /usr/share/doc/apache2-doc/manual/en. That doc is meant to be viewed with a browser but when I try to load [http://localhost/usr/share/doc/apache2-doc/manual/en/index.html](http://localhost/usr/share/doc/apache2-doc/manual/en/index.html) I get a 404 error.
 "GET /usr/share/doc/apache2-doc/manual/index.html HTTP/1.1" 404 479 "-" "Mozilla/5.0 (X11; Ubuntu; Linux i686; rv:31.0) Gecko/20100101 Firefox/31.0"

I'm in a kindof catch 22 I think. I need docs/help to fix my configs.

What/where <Directory>  settings do I need to get to those docs?? 

What command line command can I use to extract the default apache2.conf and 000-default.conf (or any others) that I might need??

I have this in my conf-enabled

<Directory "/usr/share/doc/apache2-doc/manual/">
    Options Indexes FollowSymlinks
    AllowOverride None
    Require all granted
    AddDefaultCharset off
</Directory>


so not sure why I can't get there?

I just found that I don't have DocumentRoot defined in apache2.conf but it is set in 000-default.conf
000-default.conf:       DocumentRoot /var/www/html
 
in apache2.conf I have
<Directory /var/www/>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

should that be /var/www/html  ??

lots of questions...
thanks

---

### Post by TheFu on 2014-09-02
On 14.04, a new Apache is installed by default and it is NOT enabled automatically.  There is 1 setting to allow it to work. Found it last week after doing an update from 12.04 to 14.04 here. Sorry - can't recall what the setting was - vaguely remember it was related to permissions.

Found it - **Require all granted** had to be enabled somewhere. Read the new apache docs for where to put that in your setup.

Also - many of the module names are different - had to clean up configs that pointed to the non-existing older names.

---

### Post by btodd012 on 2014-09-02
Hi,
Yes I read that. Actually I am not quite that far. I need o find the 14.04 apache2.conf default file. The conversion made some changes that mostly work - but also some strange stuff.
For example... my apache2.con has 
Include /etc/apache2/conf.d/
which inludes phpmyadmin.conf (the link).

My conf-enabled also has the exact same link to phpmyadmin.conf   - hpwever if I comment out the include and reload, I can't get access to //localhost/phpmyadmin/

My understanding was that all confs in conf-enabled would get loaded??? but apparently I have something missing - which I can't tell if I can't see a default apache2.conf for comparison.

I think this is the same problem I have not getting access to
//localhost/manual  where Alias /manual /usr/share/doc/apache2-doc/manual/

Bob





> **TheFu said:**
> On 14.04, a new Apache is installed by default and it is NOT enabled automatically.  There is 1 setting to allow it to work. Found it last week after doing an update from 12.04 to 14.04 here. Sorry - can't recall what the setting was - vaguely remember it was related to permissions.

Found it - **Require all granted** had to be enabled somewhere. Read the new apache docs for where to put that in your setup.

Also - many of the module names are different - had to clean up configs that pointed to the non-existing older names.

---

### Post by btodd012 on 2014-09-02
Haven't found my problems yet but I was able to get my default files.

cd /tmp

mkdir apache-tmp
apt-get download apache2
dpkg -x apache2_2.4.7-1ubuntu4.1_i386.deb /tmp/apache-tmp

now I have the files...
thanks to ask ubuntu and a few tips there

---

### Post by TheFu on 2014-09-02
> //localhost/phpmyadmin/

Is this an apache question or a samba question?  I don't know which URL you are seeking based on that URL - which is missing the protocol.

Also my php-fu is completely lacking. Sorry.

---

### Post by btodd012 on 2014-09-02
Its apache. Similarly, I can't access [http://localhost/manual](http://localhost/manual)

In /etc/apache2/conf-enabled I have the file apache2-doc.conf which has in it....

Alias /manual /usr/share/doc/apache2-doc/manual/


<Directory "/usr/share/doc/apache2-doc/manual/">
    Options Indexes FollowSymlinks
    AllowOverride None
    Require all granted
    AddDefaultCharset off
</Directory>


I can't access that either.... I think it is something screwy in my apache2.conf. Now that I have the default config files, I'll see what is broken.

---

### Post by btodd012 on 2014-09-04
this  thread has gotten messy and changed lives.. 
my site is now working but is too open.
I am starting a new questions.

---

