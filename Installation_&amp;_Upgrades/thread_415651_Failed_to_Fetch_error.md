---
title: "Failed to Fetch error"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by jkrumm on 2007-04-20
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

Looks like this error is pretty common. Yesterday I was told this was because of hammered servers, even though I got the exact same message when I tried to download the beta several weeks ago (for several days in a row). Today my connection seemed very fast. I zoomed through all the files and got the error message in record time (yesterday it was indeed slow).

So is this really hammered servers, or maybe some other problem?

Thanks,

John

---

### Post by jkrumm on 2007-04-21
Still the same message today...

---

### Post by Sonicgoo on 2007-04-22
I am also getting this error trying to upgrade from Dapper Drake.

It changes every time but this time it failed with this
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

---

### Post by Sonicgoo on 2007-04-22
Any word on this, any ideas, do I just have to wait?

---

### Post by jkrumm on 2007-04-22
Still the same today... Saw a few messages about getting new distribution lists and then modifying text files and saving them somewhere, but I'm a bit of a newbie to try that. I sispect I'll have to go the clean install route with a live cd, no big deal since the only thing I have to mess with are bookmarks, and I can use Google sync for that.

---

### Post by Sonicgoo on 2007-04-22
I finally tried the FTP trick in this thread 

[http://ubuntuforums.org/showthread.php?p=2511002#post2511002](http://ubuntuforums.org/showthread.php?p=2511002#post2511002)

it worked.:) 

The trick is to edit the source list changing all of the http to ftp
sudo gedit /etc/apt/sources.list

---

### Post by jkrumm on 2007-04-23
> **Sonicgoo said:**
> I finally tried the FTP trick in this thread 

[http://ubuntuforums.org/showthread.php?p=2511002#post2511002](http://ubuntuforums.org/showthread.php?p=2511002#post2511002)

it worked.:) 

The trick is to edit the source list changing all of the http to ftp
sudo gedit /etc/apt/sources.list

--------------
Ok, this is a complete newbie quiestion, but if this is a fix (one of at least a couple fixes, it seems) why isn't this changed at the list source for everyone so we don't have to edit anything and risk messing stuff up?

---

### Post by Sonicgoo on 2007-04-26
I'm a newbie as well, This was not an official fix, just a work around that someone suggested and it worked for me, so I thought I would pass on the information.

So in other words I don't know :)

---

