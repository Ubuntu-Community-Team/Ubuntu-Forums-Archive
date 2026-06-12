---
title: "Update not working"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by simpleblue on 2010-03-12
When I go to do an update the 'Downloading Package Information' where it says 'individual files' all say 0 B and either 'hit' or 'failed.'


Here is what it says:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_CA.bz2](http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_CA.bz2)  
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  
Some index files failed to download, they have been ignored, or old ones used instead.


Here is what I have for the Software sources:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) (source code)
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu)
[http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/)


Any ideas?

Thanx

---

### Post by Enigmapond on 2010-03-12
Both Google and GetDeb are notoriously slow. Maybe try going to your software sources and changing the location of your download. If you are in the States...change it to the archive at Duke.edu as I've found that to be the fastest.

---

### Post by simpleblue on 2010-03-12
> **Enigmapond said:**
> Both Google and GetDeb are notoriously slow. Maybe try going to your software sources and changing the location of your download. If you are in the States...change it to the archive at Duke.edu as I've found that to be the fastest.
I have tried and it didn't work for me..

These updates are not timing out, they are simply not updating and they are displaying 0 B as a finished result.

---

### Post by Enigmapond on 2010-03-12
If you are adding the google repo just for Chrome Browser than my suggestion would be to delete it and go with the normal launchpad repo for Chromium...I ended up doing that as google hung and didn't work for me either.

[https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/%7Echromium-daily/+archive/ppa")

---

### Post by simpleblue on 2010-03-12
> **Enigmapond said:**
> If you are adding the google repo just for Chrome Browser than my suggestion would be to delete it and go with the normal launchpad repo for Chromium...I ended up doing that as google hung and didn't work for me either.

[https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/%7Echromium-daily/+archive/ppa")
Worked like a charm!

Thank you so much!

SOLVED!! ;)

---

### Post by Enigmapond on 2010-03-12
Glad I could help...happy trails!:D

---

