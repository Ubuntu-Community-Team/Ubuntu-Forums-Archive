---
title: "Ugrading 12.04 to 12.10 failed to fetch error Australia"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by johnnyzee on 2014-04-20
I have tried multiple times to upgrade from Ubuntu 12.04 to 12.10 using Ubuntu Software Center and get failed to fetch errors as below. I have tried to change to US servers but get same message. Are geoblockers at work here again?  I also tried "do-release-upgrade" and "apt-get update."I went to 

[http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ubuntu/dists/](http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ubuntu/dists/) 

and can see the Qantal distro is available but cannot seem to get there. I would upgrade to 13.10 or 14.10 if I could do it without losing all of my settings. 

Can anybody advise?

Here is the message that I get when trying to upgrade using Ubuntu Software Center

W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Index](http://au.archive.ubuntu.com/ubuntu/dists/quantal/main/i18n/Index)  
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/restricted/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/universe/source/Sources)  404  Not Found
, W:Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources](http://au.archive.ubuntu.com/ubuntu/dists/natty-backports/multiverse/source/Sources)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by bapoumba on 2014-04-20
[http://ubuntuforums.org/showthread.php?t=2212718&p=12987167#post12987167](http://ubuntuforums.org/showthread.php?t=2212718&p=12987167#post12987167)
[http://ubuntuforums.org/showthread.php?t=2212718&p=12987176#post12987176](http://ubuntuforums.org/showthread.php?t=2212718&p=12987176#post12987176)

Please read over Elfy's and coffeecat's posts as a reply to one of yours. You have Natty repos in your sources.list that you need to remove before doing anything.

Please post the output to
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

---

### Post by fantab on 2014-04-20
If you are using 12.04 then you can upgrade directly to 14.04 through 'Update Manager'... have you tried it?

You can upgrade directly to 14.04 directly from Live 14.04 DVD/USB without losing your data and settings.
Do you have a separate /home partition?

---

