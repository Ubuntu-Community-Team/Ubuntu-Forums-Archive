---
title: "installing usking make install due to apt-get 7 pagages late"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by fgaughan on 2008-03-21
I am trying to install Newsbeuter but via apt-get its at version 0.3 while the latest is 0.8.2
[http://synflood.at/newsbeuter.html](http://synflood.at/newsbeuter.html)

when i ./config i get this error message
Checking for package sqlite3... not found

You need package sqlite3 in order to compile this program.
Please make sure it is installed.


I know its installed via apt get

so i cannot get anyfurther than this.

:(

---

### Post by ryanhaigh on 2008-03-21
```
sudo apt-get install sqlite3
```

If you are going to compile from source you may want to look at using checkinstall, 
[www.falkotimme.com/howtos/checkinstall/](www.falkotimme.com/howtos/checkinstall/) 

You may also want to see if the debian package can be installed on your system:
[http://packages.debian.org/sid/newsbeuter](http://packages.debian.org/sid/newsbeuter)

---

### Post by ad_267 on 2008-03-21
If you're compiling from source then you probably need the development package too.

Try:
```
sudo apt-get install libsqlite3-dev
```

---

### Post by fgaughan on 2008-03-21
> **ad_267 said:**
> If you're compiling from source then you probably need the development package too.

Try:
```
sudo apt-get install libsqlite3-dev
```


thanks for reply that worked but now i get the error
You need package libcurl in order to compile this program.
Please make sure it is installed.


i did a apt-get install libcurl
snd i get Couldn't find package libcurl

---

### Post by ad_267 on 2008-03-21
Do a search in synaptic for libcurl

You'll probably want libcurl3 and maybe libcurl4-openssl-dev I think but if that doesn't work try some of the other packages

---

