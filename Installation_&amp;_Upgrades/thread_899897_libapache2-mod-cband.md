---
title: "libapache2-mod-cband"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by abasel on 2008-08-24
I am needing to install libapache2-mod-cband for "web-cp"

I've tried apt-get libapache2-mod-cband but had no joy.

How do I install this module. If possible apt-get would be my preferred choice but if necessary I can also use wget and compile it.. I'd just need the steps required.

---

### Post by cariboo on 2008-08-25
I found the file you are looking for here:

[http://packages.ubuntu.com/gutsy/libapache2-mod-cband](http://packages.ubuntu.com/gutsy/libapache2-mod-cband)

This version is for gutsy, but it should work. Just download the file and double click it, gdebi should open to install it.

Jim

---

### Post by abasel on 2008-08-25
Thanks for that.

I'm using a text environment so can't double click.. can I install this using apt-get?

---

### Post by Partyboi2 on 2008-08-25
From a terminal change directory to where the download package is. Then use
```
sudo dpkg -i package 
```replace "package" with name of package.

---

### Post by 2smooth on 2008-09-05
I installed it but it gives errors:

```

apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/cband.load: Cannot load /usr/lib/apache2/modules/mod_cband.so into server: /usr/lib/apache2/modules/mod_cband.so: undefined symbol: truncf
   ...fail!

```

And i don't know if this means that [this]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463789") package has been removed or not?

---

### Post by jessedp on 2008-10-23
I ran into this same issue. After not finding a quick answer, I hacked at the mod-cband source a bit and got things working.

A patch to the source tar ball is attached. Since it appears the author's site is down, I ended up downloading a copy of it from here:

[http://www.montanalinux.org/mod_cband.html](http://www.montanalinux.org/mod_cband.html)

The link is at the bottom of the article, just before the comments section. Also, for people used to use a2enmod, you'll need to stick a "cband.load" file in /etc/apache2/mods-available/. The contents of that should simple be:
```
LoadModule cband_module /usr/lib/apache2/modules/mod_cband.so

```

That said, once I got it loaded I could not get the request/connection throttling that I wanted to use working. meh.

---

### Post by michaeldommet on 2008-11-25
i have tried the change u made but there was an error with "floor" and when i change it to floorf the error gone but the cband didnot work as usual pleas let me know what happen

---

### Post by aramyegenian on 2009-09-17
Same problem here, after digging into the code and trying to find a reason for this I found out that the math library was not being compiled in with mod_cband.so, that explains the "undefined reference". 

You have to include it in the Makefile like so:
```
APXS_OPTS=**-lm** -Wc,-Wall -Wc,-DDST_CLASS=3
```I have also attached a patch to the source code, which basically does the same thing.

P.S. This only happened for me on ubuntu 64bit, debian 64bit and ubuntu 32bit work fine.

---

