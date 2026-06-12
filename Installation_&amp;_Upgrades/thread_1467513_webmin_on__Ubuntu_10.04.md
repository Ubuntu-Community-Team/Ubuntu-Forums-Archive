---
title: "webmin on  Ubuntu 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by yosiasz on 2010-04-30
Hi there
 
Trying to install webmin on Ubuntu 10.04 I get a problem with libmd5-perl. Anyone out there has run into this problem? What is the solution to fix this missing package. It says that the package is not available.
 
Thanks

---

### Post by althof on 2010-05-01
Since my laptop always connect to the internet, there's no problem with that :d

---

### Post by penguin_patrick on 2010-05-02
me as well.  I had installed clean at work on a dev server, and ran into some similar issues, but after doing 'sudo apt-get install webmin' it told me dependency errors, do a -f install.

I did this, and it worked.

But now at home, I'm trying a 9.10 -> 10.04 upgrade, but the same procedure is not working, saying I have no install candidate for both, when I try and install libmd5-perl and webmin.

So you know, I did not have webmin on my server previously.  This is a new load, 9.10 clean, then upgrade to 10.04.  I may try a clean 10.04 now, if we don't get a solution soon.

---

### Post by penguin_patrick on 2010-05-02
found a solution:

on this thread:
[HTML]http://ohioloco.ubuntuforums.org/showthread.php?t=1433581[/HTML]

there's a link to the download of libmd5-perl for jaunty, but also karmic.  So I went to the karmic page, did a download:

```
wget http://mirrors.kernel.org/ubuntu/pool/universe/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb
```

then, install libmd5-perl;

```
sudo dpkg -i libmd5-perl_2.03-1_all.deb
```

then, install webmin;

```
sudo dpkg -i webmin_1.510_all.deb
```

It now installs webmin, and is working correctly.

---

### Post by computerman88 on 2010-05-03
I am also trying to install webmin on Ubuntu 10.04 server but I get a dependency error of webmin depends on apt-show-versions. How do I fix this?

---

### Post by Shark_AtK12 on 2010-05-04
> **penguin_patrick said:**
> found a solution:

on this thread:
[HTML]http://ohioloco.ubuntuforums.org/showthread.php?t=1433581[/HTML]there's a link to the download of libmd5-perl for jaunty, but also karmic.  So I went to the karmic page, did a download:

```
wget http://mirrors.kernel.org/ubuntu/pool/universe/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb
```then, install libmd5-perl;

```
sudo dpkg -i libmd5-perl_2.03-1_all.deb
```then, install webmin;

```
sudo dpkg -i webmin_1.510_all.deb
```It now installs webmin, and is working correctly.

Thanks, was having this same problem on 10.04 Server

---

### Post by EarthMind on 2010-05-07
Yep, me too. Thanks for the solution.

---

### Post by slacker2 on 2010-05-20
> **computerman88 said:**
> I am also trying to install webmin on Ubuntu 10.04 server but I get a dependency error of webmin depends on apt-show-versions. How do I fix this?

I had this and ran:

```
sudo apt-get -f install
```

---

