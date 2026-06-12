---
title: "PHP 5.2.x on Ubuntu 6.06.1-Server (Dapper Drake)"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by mr_tea on 2007-10-12
Ok so I am looking to use a php application that requires php 5.2... when I apt-get install php5 from the command line 5.1.6 installs on my system and there is no upgrade available which leads me to believe there is no repository for it...  I have tried to compile the new version but it fails on something about xml2, which is a separate issue...  I guess i want to be able to use apt-get so that if they do decide to make a repository for it then i won't hose apt-get...  any suggestions?

---

### Post by mr_tea on 2007-10-15
anyone?

---

### Post by cg` on 2007-10-18
I'm currently running 6.06 LTS, and can only seem to get 5.1.2

```

chris@server:~$ php -v
PHP 5.1.2 (cli) (built: Jul 17 2007 17:32:48)
Copyright (c) 1997-2006 The PHP Group
Zend Engine v2.1.0, Copyright (c) 1998-2006 Zend Technologies

```

Is there a way to obtain at least 5.1.3 or above on 6.06 LTS?

Thanks :)

---

### Post by cg` on 2007-10-25
Sorry to bump this :)

Alternatively contemplating a fresh install to 7.10 server, but like 6.06 's support / LTS.

Cheers.

---

### Post by mozmac on 2008-02-19
I would like to know the answer to this.  I am running 6.06 server and need to upgrade PHP above 5.1.2.  I do not want to compile PHP from source...that's what started my problems in the first place.  Is there a way to install a newer version of PHP through apt?

---

### Post by hsteckylf on 2008-04-06
Running the 6.06 LTS for a server and not being able to update PHP beyond 5.1.2 is a major issue. The upcoming [symfony]("http://www.symfony-project.org/") framework (1.1) requires PHP 5.1.3 or greater and I have not been able to find any solutions to do this without upgrading the OS to a non-LTS version. Once 8.04 LTS comes out, I will do tests and eventually upgrade to that, but not being able to get what I need now is very frustrating.

Does anyone have any solutions for this problem now?

---

### Post by kneecapd on 2008-05-09
I'm trying to do the same thing.  I can't get above PHP 5.1.2 on Ubuntu 6.06.2 LTS. 

Seems crazy that we can't upgrade higher than 5.1.2 ?

---

### Post by hsteckylf on 2008-05-10
I ended up just pushing my install to 6.10 for a month until 8.04 came out and then going to that. It is only a development machine so that isn't the end of the world, but this is something that is going to continue to be an issue for people using Ubuntu in server mode and should be addressed.

---

### Post by Janghou on 2008-06-02
I don't understand this either, why can't we update PHP on Dapper Drake.

What is the use of LTS support for 3-5 years on a server if you can't update the programs that make a server a server?
IMHO the long term support is more or less useless then. I feel it's not a recommendation for using UBUNTU servers in the end.

It doesn't make any sense to me. I don't want to change the OS, I want simply update programs running on it.

It's not only about added features in PHP, it's also about patching and security-issues. Every new release on PHP is recommended, and bugs are fixed. 

I think ubuntu should reconsider their strategy and deliver new binaries for server-software updates. I don't see why that's so difficult.

That will make LTS like it promises.

Untill then, is this then the way to go:
[http://www.howtoforge.com/forums/showthread.php?t=20436](http://www.howtoforge.com/forums/showthread.php?t=20436)

---

### Post by loeppel on 2008-06-24
Need this too.
Tried to get backports via prevu but  the same libapr1 Problem descibed in [launchpad entry]("https://bugs.launchpad.net/dapper-backports/+bug/123753"). 

Any suggestions?

Greets,
loeppel

---

