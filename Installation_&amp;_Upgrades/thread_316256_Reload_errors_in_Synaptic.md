---
title: "Reload errors in Synaptic"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by elysium069 on 2006-12-10
I just installed ubuntu, I am attempting to update some of the software. I get this error every time I attempt to refresh.

[http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]

How do I fix this?

---

### Post by bscbrit on 2006-12-10
The problem might not be on your computer but in the server that holds the repos.  

Can you access the internet using Firefox?  Are you certain that you have a working internet connection?

---

### Post by elysium069 on 2006-12-10
I am able to access those particular files in FireFox.

---

### Post by bscbrit on 2006-12-10
That's funny, because when I click on the links in your last post I get

```
 
Object not found!

The requested URL was not found on this server. The link on the referring page seems to be wrong or outdated. Please inform the author of that page about the error.

If you think this is a server error, please contact the webmaster.
Error 404
us.archive.ubuntu.com
Sun Dec 10 13:15:50 2006
Apache/2.0.55 (Ubuntu) 

```

Try it.

---

### Post by elysium069 on 2006-12-10
Not sure why, but it looks like it is adding a : at the end of the url.

---

### Post by bscbrit on 2006-12-10
Does it happen on all entries in your repos list, just those from a specific site or is there no obvious pattern to which ones are rejected?

Have you tried accessing a different server?

---

### Post by elysium069 on 2006-12-10
It seems to be rejecting everything. There have been a few other threads posted on this topic, but no one has posted a fix.

---

### Post by bscbrit on 2006-12-11
I would try using a different server for your repos.  If you are using a USA server, try one in Canada which shouldn't be too much slower, or anywhere else in the world if you are not in a rush...:-D

---

