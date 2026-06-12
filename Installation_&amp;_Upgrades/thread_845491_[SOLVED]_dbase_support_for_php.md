---
title: "[SOLVED] dbase support for php"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by jwf0020 on 2008-06-30
I am running a LAMP ubuntu server and I need to be able to read from a .dbf file. This can be done by installing the dbase extension into php. I currently have php 5.1.2 and have tried everything I can think of to enable dbase.

I have tried running ./configure --enable-dbase

I have copy/pasted the dbase.so into my extension library

I have modified the php.ini file to read the dbase.so extension

And I have made sure that I am modifing the correct directories by looking at phpinfo()

And I still get " Fatal error: Call to undefined function dbase_open() " when I try to open a .dbf file.

Any suggestions? 

I'm wondering if I can just get the dbase class source code and just copy/paste into my .php file to "hardcode include" it. (if that makes sense)

---

### Post by Partyboi2 on 2008-06-30
Maybe [[COLOR=Blue]this[/COLOR]]("http://linuxhints.blogspot.com/2006/06/i-needed-to-have-php-compiled-with.html") will be of use.

---

### Post by jwf0020 on 2008-07-01
Thank you! I have spent way too much time trying to figure this out. Problem is solved.

---

### Post by jules98 on 2008-08-25
Hi all,

As I haven't the possibillty to re-compile PHP, I had to use another way to be able to use the dbase extension.

Here is the procedure:

1. Idendify what you need:
> 
root@gandalf:~# dpkg --status php5-common | egrep '^(Version)|(Architecture)'
Architecture: amd64
Version: 5.2.4-2ubuntu5.3
root@gandalf:~# 


2. Fetch a package which match your system:
- I have use the site
[http://www.rpmfind.net/]("http://www.rpmfind.net/")
- Select "Go directly to the RPM database" and "Search"
- Enter "php5-dbase" and go...
- From the list, select a package as close as possible of your system (for me: "php5-dbase-5.2.4-10.x86_64.rpm").
- Download the package.
- Copy it in a temporary place (like "/tmp").

3. As it's an "rpm" package, you need Alien in order to use it. Install Alien with:
> 
root@gandalf:~# apt-get install alien
Reading package lists... Done
Building dependency tree
Reading state information... Done

... bla bla bla ...

Setting up rpm (4.4.2.1-1ubuntu6) ...

Setting up alien (8.69) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@gandalf:~#


4. Now you need to open the rpm to get the files you need:
> 
root@gandalf:/tmp# alien -s php5-dbase-5.2.4-10.x86_64.rpm
Directory php5-dbase-5.2.4 prepared.
root@gandalf:/tmp# 


5. Check that the files you need are present:
> 
root@gandalf:/tmp# find . -name 'dbase.*'
./php5-dbase-5.2.4/usr/lib64/php5/extensions/dbase.so
./php5-dbase-5.2.4/etc/php5/conf.d/dbase.ini
root@gandalf:/tmp# 


5. Check that the library is able to run:
> root@gandalf:/tmp# ldd ./php5-dbase-5.2.4/usr/lib64/php5/extensions/dbase.so
        linux-vdso.so.1 =>  (0x00007fff40dfe000)
        libc.so.6 => /lib/libc.so.6 (0x00007f1c3884c000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f1c38dbe000)
root@gandalf:/tmp# 


6. Now copy the files at the right place:
> 
root@gandalf:/tmp# cp -p ./php5-dbase-5.2.4/usr/lib64/php5/extensions/dbase.so /usr/lib64/php5/20060613/
root@gandalf:/tmp# cp -p ./php5-dbase-5.2.4/etc/php5/conf.d/dbase.ini /etc/php5/conf.d/
root@gandalf:/tmp# 


7. You need to restart the apache server to activate the new module:
> 
root@gandalf:/tmp# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                         [ OK ]
root@gandalf:/tmp# 


8. Finally, check that the server is happy:
> 
root@gandalf:/tmp# tail /var/log/apache2/error.log
...
[Mon Aug 25 11:08:01 2008] [info] removed PID file /var/run/apache2.pid (pid=29440)
[Mon Aug 25 11:08:01 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Aug 25 11:08:12 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Mon Aug 25 11:08:12 2008] [info] Server built: Jun 25 2008 13:54:43
root@gandalf:/tmp# 


9. Now you should be able to use the dbase extension...

Good luck, Jacques-D.

---

### Post by Johnsie on 2009-07-29
I've submitted a blueprint to try and get .dbf capabilities out of the box. If you're interested in getting this implemented please subscribe to the blueprint:

[https://blueprints.launchpad.net/ubuntu/+spec/apache2-php-dbf-support](https://blueprints.launchpad.net/ubuntu/+spec/apache2-php-dbf-support)

---

### Post by DataMatrix on 2010-07-06
[http://www.marksanborn.net/php/adding-dbase-support-to-php5-on-ubuntu/](http://www.marksanborn.net/php/adding-dbase-support-to-php5-on-ubuntu/)
This is a very helpful article on the subject, note that you need to download PHP 5.2.13 from php.net, since there isn't dbase included in the newer sources.
When compiling dBase from the older source I've received error about duplicate "STATIC" on lines from 758 to 821. Remove the "static" statement and recompile, it works like a charm :D

---

### Post by spencerliechty on 2013-03-24
Wanted to throw in a faster way to install dbase, without rebuilding php from source.

1. Install PECL
[http://www.mkfoster.com/2009/01/04/how-to-install-a-php-pecl-extensionmodule-on-ubuntu/](http://www.mkfoster.com/2009/01/04/how-to-install-a-php-pecl-extensionmodule-on-ubuntu/)

2. Install dbase package using PECL
> sudo pecl install dbase

3. Add "extension=dbase.so" to your php.ini file

---

### Post by overdrank on 2013-03-24
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

