---
title: "cannot update packages/install new programs"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by cjbmtb on 2006-11-15
All,

Loving the ease of use so far - I have pretty much everything working but have not yet conquered a problem that will not go away!

I have setup proxies correctly, disable ipv6, changed the sources.list file for apt, and still cannot get packages to download/update via apt, synaptic or the add/remove from the applications window.  My error is of the following (cut and pasted sample):

...

[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz:) 401 Unauthorized
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz:) 401 Unauthorized
[http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz:) 401 Unauthorized

EOF

Any ideas?  Everything else is working and I am pleased so far.  I would just like to be able to keep system programs up to date!

Thanks!

---

### Post by leikao on 2006-11-16
Make sure you could access to the website: [http://archive.ubuntu.com/](http://archive.ubuntu.com/).
You can ping it in the terminal, if lots of the packages lost, pls change your sources.list to another source, and try anain.

Enjoy.

---

### Post by cjbmtb on 2006-11-16
Pinging that host is not a problem.  I have tried various sources.lists that have been posted to this forum.  Somewhat stuck on upgrade right now!

---

### Post by taurus on 2006-11-16
Are you sure you have the proxy thing configured correctly?

---

### Post by bapoumba on 2006-11-16
apt checks /etc/apt/apt.conf file for proxy. You should have in that file :
ACQUIRE {http:: proxy "http://<proxy>:<proxy_port>"};

skip the space between http:: and proxy (the smiley thing ;))

---

### Post by cjbmtb on 2006-11-17
Still no luck...I have the proxy settings enabled and am having problems.  I thought it could be that edgy is so, well, edgy ;) 

Anyhow, in my hast, I installed dapper.  I have had to go through and redo my settings again to enable networking.  Now, my ssh and telnet to other machines are getting blocked!  I had setup network proxy in edgy via the gui, but do not see a similar feature.  I have put export http_proxy and ftp_proxy lines in my .bashrc (and verified they are set with echo $arg.)

Oh, and still getting 401 Unauthorized in both apt and synaptic.  Taking my machine to work to see if it is just my router.

Thanks!

---

### Post by cjbmtb on 2006-11-17
Great news!  Package updates are working now...as I began to realize last night, the problem is how my home router is configured.  I have ubuntu completely updated (even was able to upgrade back to edgy - go figure :) 

So, now I will take my laptop home, reconfigure my router to work with my new distro and use my linux box for what it was meant to do - work!

-Thanks!

---

