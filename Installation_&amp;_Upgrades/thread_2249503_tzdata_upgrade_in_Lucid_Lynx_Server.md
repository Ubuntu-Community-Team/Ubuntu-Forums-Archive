---
title: "tzdata upgrade in Lucid Lynx Server"
date: 2014-10-22
forum: Installation &amp; Upgrades
---

### Post by bigfatkill on 2014-10-22
Hi all,

According to Ubuntu website, Ubuntu 10.04 Lucid Lynx Server
will be supported until April 2015. **But how could I update tzdata?**

There will be Russian zone changes coming up on October 26th,
so I need tzdata update for a couple of my old 10.04 Russian servers.
Ubuntu 12.04 Precise Pangolin already has this update in repo, but 
10.04 have not. [COLOR=#ff0000]My clock on Russian servers will be screwed, if I will
not apply an update on time.[/COLOR]:(

What should I do? Go straight to developers or just do a dirty trick with installing non-Lucid package on Lucid?

Thank you!

---

### Post by papibe on 2014-10-22
Hi bigfatkill. Welcome to the forum ):P

I'd recommend creating a bug on [https://launchpad.net/](https://launchpad.net/)

Regards.

---

### Post by mörgæs on 2014-10-23
You will not necessarily get the new tzdata. 
'Supported' means that security bugs are fixed. Adding new functionality is backporting which may or may not happen.

---

### Post by Impavidus on 2014-10-23
I got that update today (+ another for some Belarussian changes) on my trusty laptop and it was labeled as an important security update. Guess it could be important in some cases and definitely urgent. Just checked the server and my mirror (which is the dutch one) has the tzdata updates also available for 10.04 since early this morning. Just check again, it should percolate to all mirrors in a few hours.

---

### Post by papibe on 2014-10-23
It seems the update is being distributed to Lucid 10.04.

From my 10.04 server:
```
$ apt-cache policy tzdata
tzdata:
  Installed: 2014e-0ubuntu0.10.04
  Candidate: **2014i-0ubuntu0.10.04**
  Version table:
     2014i-0ubuntu0.10.04 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
        500 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
 *** 2014e-0ubuntu0.10.04 0
        100 /var/lib/dpkg/status
     2010i-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages

```
and then:
```
$ aptitude changelog tzdata | head

tzdata (**2014i-0ubuntu0.10.04**) lucid; urgency=critical

  * New upstream release with zone changes in 4 days for Belarus.

 -- Adam Conrad <adconrad@ubuntu.com>  Wed, 22 Oct 2014 17:22:43 -0600


```

---

### Post by bigfatkill on 2014-10-23
Wow! **Thank you, comrades!**
Issue closed! :guitar:

---

