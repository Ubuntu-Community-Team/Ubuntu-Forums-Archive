---
title: "kubuntu 7.10 dolphin bug? error (changes to root user)"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by bone2006 on 2007-10-18
Not sure if I'm alone here, but when I use dolpin in the new kubuntu 7.10 that I just got today, if I look at the right side it says open in root, when I open in root then do some work and close it it seems to modifiy a file with root.

this directory:
~/.kde/share/apps/d3lphin

has a file called bookmarks.xml and when I close dolpin everything works just fine.  Once I open anything with root user it changes the premissions when I go to that file and run

stat bookmarks.xml the group and user is now root. So when I reopen the file manager as a regular user and then close it gives me the error.

I'm suspecting because once I open dolpin with root, it then modifies bookmarks.xml with the root user and root group, then it creats a backup with bookmarks.xml.bak both have to have root access, so the regular user now keeps getting this error.

Or am I alone?

---

### Post by bone2006 on 2007-10-18
The way I fixed this error is 

sudo chown user:gropu bookmarks.xml and also to sudo chown user:gropu bookmarks.xml.bak

But if I ever open the file manager again in root and close it..........the problem is there again.  Since I changed the premissions though right now I'm alright............still seems like a bug to me.

---

### Post by screaminj3sus on 2007-10-19
> **bone2006 said:**
> The way I fixed this error is 

sudo chown user:gropu bookmarks.xml and also to sudo chown user:gropu bookmarks.xml.bak

But if I ever open the file manager again in root and close it..........the problem is there again.  Since I changed the premissions though right now I'm alright............still seems like a bug to me.

same thing happens here, I deleted the bookmarks.xml file which fixes it until nest time it happens.

---

### Post by bone2006 on 2007-10-20
hopefully the bug will be fixed.  I couldn't find it anywhere in [https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/)
but not sure if kubuntu bugs go in there as well

---

### Post by sirwitti on 2007-10-22
bug report can be found here:

[_https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/136458_]("https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/136458")

 but no sign of any persistant workaround/solution for this right now
have fun, witti

---

### Post by sirwitti on 2007-10-22
hi again!
i just found out that the bug report i referred to is a duplicate of another bug which is the real source of the problem:
[https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/155032]("https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/155032")

according to this report the problem is kdesu not dolphin. so, a temporary (but not quite good) workaround for this is to remove the kdesu package by executing:
```
sudo apt-get remove kdesu
```

another temporary solution is a fixed version of kdesu that Frode M. Døving posted.
just read the bug report for more information.
so, i hope that helps for now, witti

---

### Post by Maragato on 2007-12-05
Is there any official solution for this by now?

---

### Post by bone2006 on 2007-12-15
maybe it's just me, but it seems like more effort is put into the gnome version, so bugs that are only associated with the KDE version of kubuntu seem not to get the same attention.  Could be just my take.

---

