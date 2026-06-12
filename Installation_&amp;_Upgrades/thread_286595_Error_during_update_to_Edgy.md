---
title: "Error during update to Edgy"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by ScottSatkin on 2006-10-27
When I update using:
```
gksu "update-manager -c"
```
I get the following error:
> 
Error during update
A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg) Temporary failure resolving ‘packages.freecontrib.org’
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
This has occurred on two machines both running dapper.  They use separate ISPs for their internet connections; therefore, I do not think it is a "network problem" on my end.

I cannot ping or dig freecontrib.org.

Anyone else getting this error?  Any advice?

---

### Post by vibestriton on 2006-10-27
freecontrib.org is down.  comment it out.

gksudo gedit /etc/apt/sources.list

add "#" before the freecontrib.org line(s)

---

### Post by ScottSatkin on 2006-10-27
What about:

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

---

### Post by vibestriton on 2006-10-28
That server is fine...

Do this...

```
sudo apt-get install --reinstall gzip
```... and try again.

---

### Post by ScottSatkin on 2006-10-28
I tried:
```
sudo apt-get install --reinstall gzip
```
However, I still get the same error:
> 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Any further advice?

---

### Post by damianvila on 2006-10-29
I'm having this problem also.
There's no solution to it so far...
:( 
I hope I don't have to reinstall Ubuntu.
If anybody's got a better idea, I'll be waiting.
Regards,

D.

---

### Post by damianvila on 2006-10-30
These threads appear to be the same problem...
[http://www.ubuntuforums.org/showthread.php?t=112970](http://www.ubuntuforums.org/showthread.php?t=112970)
[http://www.ubuntuforums.org/showthread.php?t=285242](http://www.ubuntuforums.org/showthread.php?t=285242)
[http://www.ubuntuforums.org/showthread.php?t=287345](http://www.ubuntuforums.org/showthread.php?t=287345)
Any help?

D.

---

### Post by damianvila on 2006-10-30
More related threads:
[http://www.ubuntuforums.org/showthread.php?t=287789](http://www.ubuntuforums.org/showthread.php?t=287789)
[http://www.ubuntuforums.org/showthread.php?t=286084](http://www.ubuntuforums.org/showthread.php?t=286084)

D:

---

### Post by 5h4rk on 2006-11-16
So there is nobody can help us out?

---

### Post by damianvila on 2006-11-17
In my case the error dissapeared a few days later.
Regards,

D.

---

