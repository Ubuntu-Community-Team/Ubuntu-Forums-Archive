---
title: "Upgrade Bind from 9.4.2 to 9.8.1?"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by Jim.Armstrong on 2012-01-04
I need to upgrade Bind and I want to keep my config files intact it's been working great for 3 years now.  I just have the server and DNS installed so no gui it's all cmd line.

I've ran apt-get update.
Can you upgrade and keep your config files intact?
If you can what's the proper syntax for the command?  I'm guessing there's some switches.  
Or is it as simple as apt-get upgrade?
  

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
uname -m
i686
uname -a
2.6.24-19-server #1 

named -v 
Bind 9.4.2-P2

---

### Post by Jim.Armstrong on 2012-01-05
Is there additional info required to answer my question?

---

### Post by Jim.Armstrong on 2012-01-22
My bad it's Bind 9.7. I did a fresh install of 10.4 and installed Bind. Then sftp'd over my named.conf.options and named.conf.local from the old box to the new one.  Ran into a bit of a hitch with logging because of an apparmor permission issue.  Changed by named.conf.local file for logging from /var/log/bind to var/log/named.  And chown from root to bind.  

It's all good now.

---

