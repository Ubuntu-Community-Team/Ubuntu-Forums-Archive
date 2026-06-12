---
title: "PHP4 on Hardy?"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by fatagnus on 2008-05-16
I know it's old, obsolete, outdated, uncool, not very 2.0, etc.. but I have applications that aren't trivial to migrate to php5 and doing that right now is not an option.

Can I install PHP4 on 8.04? It doesn't show in the repos, and I'm not sure there won't be any problems to compile it myself (since it may rely on old libraries not available in the repos again).

I did a google search for it, but the best I could find was a page in chinese, and, since I don't understand it (sorry, can't learn it right now) I thought it was a good idea to ask about it here.

---

### Post by Tato on 2008-05-26
I found these pages:
[http://www.jsanroman.net/2008/05/06/php5-y-php4-tambien-conviven-en-mi-ubuntu/](http://www.jsanroman.net/2008/05/06/php5-y-php4-tambien-conviven-en-mi-ubuntu/)
[http://my.opera.com/zomg/blog/2007/08/12/running-both-php4-and-php5](http://my.opera.com/zomg/blog/2007/08/12/running-both-php4-and-php5)

This is what I did:
1. Download _libzzip-0.12_ from one of the mirrors in:
[http://packages.debian.org/etch/i386/libzzip-0-12/download](http://packages.debian.org/etch/i386/libzzip-0-12/download)

2. Choose a repository and add it to synaptic:
[http://www.dotdeb.org/mirrors](http://www.dotdeb.org/mirrors)

3. Reload/update your packages list and install _php4-cgi_ and any other php4 extension you may need like _php4-mysql_, etc.

4. Activate the apache actions module with
```
sudo a2enmod actions
```

5. Finally write a _.htaccess_ file inside your website directory with
```
AddHandler php-script .php
Action php-script /cgi-bin/php4
```

This will make all the php files inside that directory and subdirectories to use php4.

You can check the links for more information.

---

### Post by prantap@gmail.com on 2008-07-16
Hi, 

After following these steps would it replace a working instance of php5? 

I want to run an instance of both php4 (for old applications) and php5 for current development. 

Thanks,
Prantap

---

### Post by father time on 2008-09-04
Message Deleted.

---

