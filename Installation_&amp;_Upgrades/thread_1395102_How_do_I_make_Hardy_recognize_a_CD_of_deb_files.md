---
title: "How do I make Hardy recognize a CD of deb files?"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by SunKing2 on 2010-01-31
I'm using Hardy Heron. I'd like to keep using it.  I mean forever.

I have several old PCs, and in the past few years I've installed 8.04 several times.  Every time I install, it downloads about 184 updates... a slow process. 

I would like to put all the .deb files on a CD (or flash drive) so that future installs won't need to download these updates.

Question 1:  How do I get a newly installed version of Hardy Heron to recognize that there are files on the CD, and so use them rather than downloading the files.  I think that maybe just copying the files to /var/cache/apt/archive might work.  Is this true?

Question 2: I once loved version 7 of Ubuntu like I love 8.04 now.  But when I try to install it, it won't update anything anymore and it seems unable to find any additional software for version 7.  Now I've abandoned version 7, but is there a way to download hundreds of deb files for Hardy Heron, save them to a CD, to ensure that I can continue to use Hardy Heron in say, the year 2012, and have access to all of its non-standard packages, and still be able to install other packages which are located on CD?

---

### Post by oldos2er on 2010-01-31
If you have *deb files on a cd, you can install them with either dpkg or gdebi. For example ```
sudo dpkg -i /media/cdrom/*deb
```

Or, when the cd is mounted, double-click on a *deb, and gdebi will open and allow you to install it.

---

### Post by amac777 on 2010-01-31
All the old releases of Ubuntu are still available here:

[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

To use them, you need to update your apt sources (/etc/apt/sources.list) file to point to that url instead of whatever mirror you were using.

---

### Post by oupamster on 2010-01-31
just to add on, how about using Apt-on-CD?

---

