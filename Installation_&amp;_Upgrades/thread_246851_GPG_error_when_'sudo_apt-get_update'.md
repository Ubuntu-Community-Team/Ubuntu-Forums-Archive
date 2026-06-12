---
title: "GPG error when 'sudo apt-get update'"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by Dislimit on 2006-08-29
I saw sb. posted similar threads but never seen a good answer.

GPG error happens when a do a apt-get update.
After downloading some update package it will notify:
```

...
Hit http://ubuntu.mirrors.tds.net breezy-updates/universe Packages
Hit http://ubuntu.mirrors.tds.net breezy-updates/multiverse Packages
Fetched 644kB in 20s (31.6kB/s)
Reading package lists... Done
W: GPG error: http://ubuntu.mirrors.tds.net breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ubuntu.mirrors.tds.net breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ubuntu.mirrors.tds.net breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```

Though I'm now using mirror sites. It also happens when I use officailly offered source list with Ubuntu5.10. Btw, I've no time to upgrade to Dapper recently, still using 5.10. And the problem was there even before Dapper was released.
Sometimes I do
```

cd /etc/apt
del sources.list[INDENT][/INDENT]# Just put it into .Trash
sudo apt-get update[INDENT][/INDENT]# Update with an empty list.
cp ~/.Trash/sources.list .
sudo apt-get update

```
And the problem would go away. And appear some days later.
But in recent few months it doesn't work. I didn't post it earlier
coz I've been busy and I can still download most of update packages.

As the best desktop Linux so far, I hope Ubuntu will give an
answer.

Here's current my sources.list.
```

deb http://ubuntu.mirrors.tds.net/ubuntu breezy main restricted universe multiverse 
deb http://ubuntu.mirrors.tds.net/ubuntu breezy-security main restricted universe multiverse
deb http://ubuntu.mirrors.tds.net/ubuntu breezy-updates main restricted universe multiverse
#deb http://ubuntu.mirrors.tds.net/ubuntu breezy-backports main restricted universe multiverse
deb-src http://ubuntu.mirrors.tds.net/ubuntu breezy main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

#deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

#deb http://security.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

```

---

### Post by Dislimit on 2006-09-01
Nobody knows? Not even the mods?

---

### Post by randell6564 on 2006-09-01
> **Dislimit said:**
>  
Here's current my sources.list.
```

deb http://ubuntu.mirrors.tds.net/ubuntu breezy main restricted universe multiverse 
deb http://ubuntu.mirrors.tds.net/ubuntu breezy-security main restricted universe multiverse
deb http://ubuntu.mirrors.tds.net/ubuntu breezy-updates main restricted universe multiverse
#deb http://ubuntu.mirrors.tds.net/ubuntu breezy-backports main restricted universe multiverse
deb-src http://ubuntu.mirrors.tds.net/ubuntu breezy main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

#deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

#deb http://security.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

```

Hi!  Why don't you try uncommenting (removing the # sign at the beginning of the repositories that have one)? Then try again!

---

### Post by webjames on 2006-11-28
hi i have the same problem, i don't think it is to do with the software lists.

keep an eye on this thread, i hope to find a solution:

> [http://www.ubuntuforums.org/showthread.php?t=308638](http://www.ubuntuforums.org/showthread.php?t=308638)

regards,

James

---

