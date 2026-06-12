---
title: "Constant apt-get install problems"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by FlyingIsFun1217 on 2007-03-31
Hey,

Upon attempt to install a few different pieces of software using apt-get install, I always seem to get these error messages:

> 
/bin/sh: /usr/sbin/dpkg-preconfigure: not found
dpkg: `install-info' not found on PATH.
dpkg: `update-rc.d' not found on PATH.
dpkg: 2 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)


Thanks for your continuous help!
FlyingIsFun1217

---

### Post by 1/0 on 2007-03-31
What paths do you have?

```

sudo su
echo $PATH

```

---

### Post by FlyingIsFun1217 on 2007-03-31
> **1/0 said:**
> What paths do you have?

```

sudo su
echo $PATH

```

> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games


Thanks for your help!
FlyingIsFun1217

---

### Post by 1/0 on 2007-03-31
What happens if you do:

```

sudo su
source ~/.profile 
apt-get upgrade

```
?

---

### Post by FlyingIsFun1217 on 2007-03-31
> **1/0 said:**
> What happens if you do:

```

sudo su
source ~/.profile 
apt-get upgrade

```
?

> 
The following packages will be upgraded:
  dvd+rw-tools mozilla-thunderbird
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.9MB of archives.
After unpacking 922kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main mozilla-thunderbird 1.5.0.10-0ubuntu0.6.10 [10.8MB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main dvd+rw-tools 7.0-6~dapper2 [138kB]
Fetched 10.9MB in 1m8s (161kB/s)                                               
/bin/sh: /usr/sbin/dpkg-preconfigure: not found
dpkg: `install-info' not found on PATH.
dpkg: `update-rc.d' not found on PATH.
dpkg: 2 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)


Seems that it does that anytime I try and install something... ; /

FlyingIsFun1217 :)

---

### Post by FlyingIsFun1217 on 2007-03-31
I think before that I accidentally deleted /usr/sbin before... Is this what is causing it? If so, how can I go around retreiving /usr/sbin, or creating a new one (does it matter that the contents are gone?).

Thanks!
FlyingIsFun1217

---

### Post by 1/0 on 2007-03-31
Oooops! Deleting /usr/sbin could definitely explain your problems what's in /usr/sbin?

```
ls /usr/sbin
```

---

### Post by FlyingIsFun1217 on 2007-03-31
ls: /usr/sbin: No such file or directory


D:

Thanks again
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2007-03-31
Would simply making a /usr/sbin solve the problem, or are there files that were in it that need to be recovered?

Thanks!
FlyingIsFun1217

---

### Post by 1/0 on 2007-03-31
Now that's a new one to me... You can create the folder /usr/sbin by:

```
sudo mkdir /usr/sbin
```

But you can't retrieve all files that were in the folder by a command. I just switched from Gentoo so I'm not 100 on Xubuntu yet. Perhaps there is a repair function on the install cd. You could try the following but I'm quite sure it'll fail:

```

sudo apt-get install ubuntu-desktop

```

Take the installation cd and copy the files from /usr/bin to the folder on your computer. Hopefully this will do. The most important file is probably dpkg-preconfigure. Its probably possible to find the files on some server but it will probably be much more difficult than using the cd. I'm just guessing here.

In worst case you're looking at a reinstall but I think you should be able to avoid that by somehow getting that dpkg-preconfigure file and then install ubuntu-desktop as above.

There's always a solution the question is where, what and how. And flying is really bad for the environment by the way ;-)

---

### Post by FlyingIsFun1217 on 2007-03-31
Ok, I'll see if I can't just copy over the files from the cd, and if not, I'll just try and get it from somebody else with Ubuntu.
Apparently Linux isn't quite idiot-proof ;)

Thanks for the help :) (and btw, Flying's fun though, so... :P )
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2007-03-31
> **1/0 said:**
> 
Take the installation cd and copy the files from /usr/bin to the folder on your computer. Hopefully this will do. The most important file is probably dpkg-preconfigure. Its probably possible to find the files on some server but it will probably be much more difficult than using the cd. I'm just guessing here.


Boy would I have loved it to be that easy :)
It seems that the CD I have is set up something like this:

> 
-bin
--chrome
---aggreg8
---overlayinfo
---...
--components
---...
--defaults
---autoconfig
---pref
---profile
---wallet
--greprefs
---...
--ipc
---modules
--kplugins
---...
--plugins
---...
--res
---builtin
---dtd
---entitytables
---fonts
---html
-casper
--..
-disctree
--app_img
---...
--en
---...
--incl
---css
---img
---js
-dists
--edgy
---main
---restricted
---...
--stable
---main
---restricted
---...
--unstable
---same as above two
-install
--...
-isolinux
--...
-pics
--...
-pool
--main
---bucha directories named with letters
--restricted
---same as above one
-preseed
--...
-programs
--abiword
--firefox
--etc.
-ubuntu
--nothing? Just keeps going back to main cd list...


Is it possible that you (or someone else) could just email (send somehow) the basic files needed for the /usr/sbin?

Thanks again for your help!
FlyingIsFun1217

---

### Post by 1/0 on 2007-03-31
I could mail at least some of the files if I get a mail address. Otherwise try to install these files (you have a i386 or i586 or i686 computer, right?):

[ftp://ftp.sunet.se/pub/Linux/distributions/ubuntu/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb](ftp://ftp.sunet.se/pub/Linux/distributions/ubuntu/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb)

[ftp://ftp.sunet.se/pub/Linux/distributions/ubuntu/ubuntu/pool/main/d/dpkg/dpkg_1.13.22ubuntu7_i386.deb](ftp://ftp.sunet.se/pub/Linux/distributions/ubuntu/ubuntu/pool/main/d/dpkg/dpkg_1.13.22ubuntu7_i386.deb)

---

### Post by 1/0 on 2007-04-03
How is it progressing for you?

---

