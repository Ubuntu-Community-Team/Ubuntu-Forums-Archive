---
title: "PHP5 not parsing web .php files after upgrade--need serious help quickly"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by jwwetzel on 2007-07-04
Hi all--

I'm running Ubuntu x64 server edition, 2.6.15-28-amd64-server.

I had php5.1.2 installed, but I wanted to upgrade to at least php5.1.4 in order to start fooling around with the google calendar api.

this is where the problems began.

i ran:
```

sudo apt-get update
sudo apt-get install php5

```
but it said "up to date, will not be updated"
so I searched and found this thread [http://ubuntuforums.org/showthread.php?p=1627363](http://ubuntuforums.org/showthread.php?p=1627363) which said to add 
```

deb http://packages.dotdeb.org stable all
deb-src http://packages.dotdeb.org stable all

```
to the sources.list file, which I did. then I ran update again and apt-get install and things broke.  I couldn't use phpMyAdmin anymore, it wouldn't let me access it with the root username and password.

I can access mysql with # sudo mysql

So I did some more things, and tell me if you need more information to help me solve my current problem.

I can't parse php files in my web directory.  Apache works, it serves the pages, but php5 doesn't seem to be installed properly--it's there.  It prompts me with the firefox file download to grab whatever *.php file I'm accessing.

this happend after i ran
```

sudo apt-get dist-upgrade

```

When I try to run apt-get install php5 now, it says
```

The following packages have unmet dependencies:
  php5: Depends: libapache2-mod-php5 (>= 5.1.2-1ubuntu3.8) but it is not going to be installed or
                 php5-cgi (>= 5.1.2-1ubuntu3.8) but it is not going to be installed
E: Broken packages

```

when I run php5 and libapache2 it says
```

The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: php5-common (= 5.1.2-1ubuntu3.8) but 5.2.3-0.dotdeb.1 is to be installed
E: Broken packages

```

I appreciate any help-- i apologize for the crappy state of this post, but I'm in a sort of panic mode because this needs to be hosted. Thanks thanks thanks again.

---

### Post by jwwetzel on 2007-07-04
I have MySQL 5.022 installed, and apache2 installed, but I tried to run
```

sudo apt-get remove php5

```
and it said that php5 is not installed

---

### Post by jwwetzel on 2007-07-04
I did
```

sudo apt-get remove php5-common

```

and ran

```

sudo apt-get install php5

```

and it installed perfectly and everything seemed fine, but it still doesn't parse the webpages!  is there a configuration i'm missing?

---

### Post by jwwetzel on 2007-07-04
well i solved all the issues.  thanks anyway.

---

### Post by ronswift on 2007-07-05
What was wrong and how did you resolve it. I am having the same problem after adding php5. Php4 worked fine but I needed php5 to test a new accounting application.

---

