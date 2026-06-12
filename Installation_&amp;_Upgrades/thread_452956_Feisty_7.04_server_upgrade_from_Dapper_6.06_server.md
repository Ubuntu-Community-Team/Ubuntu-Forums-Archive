---
title: "Feisty 7.04 server upgrade from Dapper 6.06 server - Apache not serving PHP"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by calenti on 2007-05-23
Hi there...I started with Ubuntu Breezy Badger server running on an old 366 Celeron with 320 MB RAM. Been working like a champ as a (slow) LAMP server, using phpmysqladmin, postnuke, etc. 

Went through the Dapper, Edgy upgrades fine by editing the source and then doing 

```
aptitude update
```
```
aptitude dist-upgrade
```


However, I did this for the Feisty distribution and the upgrade failed during the Apache restart (it was related to the 2.0 - 2.2 issue in the forums). I worked in the documentation and resolved the issue so Apache now starts but PHP pages aren't being processed - Apache tries to serve the php page to the browser.

I'm kinda stumped - I've tried aptitude update/upgrade, I've removed php and reinstalled it, and I can't get my phpmyadmin pages to serve (Apache sends them to the browser without rendering).

I know I will probably be carpet-bombed with RTFMs but I don't know what to try next. Should I look at the logs? Is there something in the configuration I need to check? Like I said, Apache seems to work fine, but I'd really like to get my phpmyadmin and postnuke site back. It's a little worrisome that I don't see any posts about this when searching for "feisty upgrade php" - I hope my fubar is not unique.

I also don't want to clobber the server and reformat/reinstall, I have backups for the mysql database but that seems like burning down your house to find your keys ('cause they're metal, and...it's a metaphor.)

Anyway, appreciate any help and if you throw an RTFM my way I'd appreciate a pointer on which FM to R. Thanks.

---

### Post by calenti on 2007-05-23
Followup - there's another thread on this at [http://ubuntuforums.org/showthread.php?p=2710016](http://ubuntuforums.org/showthread.php?p=2710016). I posted in there that I can run PHP -version from the command line and process pages with a command php testphp.php (which contains <phpinfo();>).

---

### Post by calenti on 2007-05-23
1 more followup - I went out and looked into mods-enabled and the php5.load file had the following entry:


```

# LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

```

I removed the comment and restarted apache...no dice. Still tries to send index.php to the browser. My apache version is 2.23.

---

### Post by calenti on 2007-05-23
Answered my own question - looked at the Troubleshooting section of

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The troubleshooting section reads:

```

Troubleshooting

Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php4. It is installed when you install the php4 package, but may have been removed inadvertently by packages which need to run a different version of php. You may also need to actually enable it, by doing sudo a2enmod php4 followed by sudo /etc/init.d/apache2 restart. Be sure to clear your browser's cache before testing your site again. 

```

I did this (substituting libapache2-mod-php5 and sudo a2enmod php5, which it said was already installed and configured)  and it -still- didn't work. Then I flushed my browser cache and voila! PHP!

So I guess it was RTFM after all! :)

---

