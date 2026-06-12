---
title: "It won't let me upgrade from Edgy"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by subliminal on 2007-05-20
Firstly i don't get the option to upgrade to Feisty from System -> Admin -> Update Manager.
If i run update-manager on the command line, i do get the option.

Then when i do click upgrade, it gets to "Modifying the Software Channels", around 48 out of 51, and then errors  with the following reasons.
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.gz) Sub-process gzip returned an error code (1)

The files are there, i've checked. Is there anyway to make it use the .bz2 versions instead of .gz? Or perhaps a way to make it just work?

---

### Post by Ciego on 2007-05-20
Same thing here .... I am getting these errors.

> Failed to fetch [http://asher256-repository.tuxfamily.org/dists/edgy/english/binary-i386/Packages.gz](http://asher256-repository.tuxfamily.org/dists/edgy/english/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/ubuntu/english/binary-i386/Packages.gz](http://asher256-repository.tuxfamily.org/dists/ubuntu/english/binary-i386/Packages.gz) 404 Not Found


EDIT:  It worked after I disabled some repositories.

---

### Post by subliminal on 2007-05-20
Yes. Although slightly different, firstly your errors appear to be to do with third party repositories, and secondly the files seem to be missing, whareas with the error codes i was getting the files exist, only they're broken or dodgy in some other way that causes gzip to error.

Unfortunatly i don't have any repositories i can remove, as my sources.list is like
```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe

```

All these are standard and normal repositories.

---

### Post by randell6564 on 2007-05-20
Make a backup copy of your /etc/apt/sources.list and then change all instances of **http:**to **ftp:**.
Then do:
```
sudo apt-get update
sudo update-manager -c
```

---

### Post by subliminal on 2007-05-20
It worked. Thanks, i don't understand exactly why, but it worked and the upgrade works, so all is good. Cheers.

---

### Post by randell6564 on 2007-05-20
> **subliminal said:**
> It worked. Thanks, i don't understand exactly why, but it worked and the upgrade works, so all is good. Cheers.
Glad to help.

---

