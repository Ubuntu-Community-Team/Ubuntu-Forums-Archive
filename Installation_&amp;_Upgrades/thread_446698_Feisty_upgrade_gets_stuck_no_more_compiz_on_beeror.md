---
title: "Feisty upgrade gets stuck: no more compiz on beerorkid"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by Iskendar on 2007-05-17
Hi all,

 I just tried to upgrade from kubuntu edgy to feisty, but something went wrong. Basically, I ran adept-manager, then used "fetch updates" which launches the distribution upgrade app. After downloading a bunch of packages, the updater launches an error window containing the following: 
```

Error during update
A problem occured during the update. This is ususally some
sort of network problem, please check your network
connection and retry.

Failed to fetch http://www.beerorkid.com/compiz/dists/edgy/Release.gpg The HTTP server sent an invalid reply header
Failed to fetch http://www.beerorkid.com/compiz/dists/edgy/main-edgy/i18n/Translation-en_US.bz2 Bad header line
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/non-free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/free/source/Sources.gz 404 Not Found
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/non-free/source/Sources.gz 404 Not Found
Failed to fetch http://www.beerorkid.com/compiz/dists/edgy/main-edgy/binary-i386/Packages.gz The HTTP server sent an invalid reply header

```

And indeed, if I check [http://www.beerorkid.com/compiz/dists/edgy/Release.gpg](http://www.beerorkid.com/compiz/dists/edgy/Release.gpg) I arrive onto a 404 page
pointing users to opencomposting.org for downloading compiz. Which would be neat if I were installing it manually, but the updater makes its own selection of packages. 

So, do any of you guys know how to do the upgrade? Do I have to find a different upgrade program? Any help?

---

### Post by syko21 on 2007-05-18
Try removing the extra repositories that are giving you the errors from the sources.list

```

sudo kedit /etc/apt/sources.list

```
and remove the repositories that are giving you the errors.

---

### Post by beerorkid on 2007-05-22
Sorry about that.  There are thousands of dead links out there.
I finally killed the repo cuz of some issues I was having with my webhost.  And it had not been updated since last november.  So really out of date.

check [opencomposting]("http://www.opencompositing.org/") for new install guides.

I edited my .htaccess to completely block the 1.5 million hits a month that were going to my old 404.php  (since they were looking for packages that did not exist, even when the repo was up)  It was sucking up some huge CPU minutes on my shared hosting.

---

### Post by zvacet on 2007-05-22
Allways do upgrade with official repos only.Comment all unoficial repos during upgrade and uncomment them after.Then you can do 
```
sudo aptitude update
```

---

