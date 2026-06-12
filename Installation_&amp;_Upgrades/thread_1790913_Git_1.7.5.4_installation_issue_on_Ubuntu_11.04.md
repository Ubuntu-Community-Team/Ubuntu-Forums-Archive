---
title: "Git 1.7.5.4 installation issue on Ubuntu 11.04"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by John1111 on 2011-06-25
When issuing the make command I get the following:

/bin/sh:  curl-config: not found
       CC daemon.o
In file included from cache.h:4:0,
                        from daemon.c:1:
git-compat-util.h:168:25: fatal error: openssl/ssl.h: No such file or directory 
compilation terminated.
make: *** [daemon.o] Error 1


If anyone could point me in the right direction, that would be great!
John

---

### Post by John1111 on 2011-06-25
I was having this problem when trying to install the download from the website.  I just tried using apt-get install and that worked, so this is no longer a problem for me, but since I don't know why exactly the download from the website didn't work, I'll leave the post for now.

John

---

### Post by Gowie47 on 2012-03-12
I had this problem on Ocelot and didn't want to install from apt-get because the version from [http://code.google.com/p/git-core/downloads/list](http://code.google.com/p/git-core/downloads/list) is a bit newer. 

After fiddling around a bit installing libcurl fixed the problem 

```
 sudo apt-get install libcurl4-openssl-dev 
```

Hope it helps somebody else out!

---

### Post by Gowie47 on 2012-03-12
I had this problem on Ocelot and didn't want to install from apt-get because the version from [http://code.google.com/p/git-core/downloads/list](http://code.google.com/p/git-core/downloads/list) is a bit newer. 

After fiddling around a bit installing libcurl fixed the problem 

```
 sudo apt-get install libcurl4-openssl-dev 
```

Hope it helps somebody else out!

---

