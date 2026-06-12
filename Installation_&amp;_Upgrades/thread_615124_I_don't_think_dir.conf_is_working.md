---
title: "I don't think dir.conf is working"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by Isolder on 2007-11-16
I don't think my dir.conf is working. I'm not used to this whole 'empty httpd.conf, apache2.conf and mods available' stuff..

In dir.conf DirectoryIndex should automatically find index.php in a dir as follows:
```

<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml

</IfModule>

```

It doesn't find it. I had to add a DirectoryIndex to the virtual hosts file..  What's up with that?
```

<Directory /var/www/>
                Options FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                DirectoryIndex index.php index.html
        </Directory>

```


I just installed ubuntu server for the first time and it has been something of an eye opener.  The initial one being that httpd.conf was empty.

---

### Post by infantiablue on 2007-11-17
Hi there, I have a same problem, I need to config the "DoucmentRoot" in httpd.conf but it is an empty file. Where can I find the real httpd.conf for Apache 2 in Ubnutu 7.10 to reconfig  ?

Thank you for your any help

---

