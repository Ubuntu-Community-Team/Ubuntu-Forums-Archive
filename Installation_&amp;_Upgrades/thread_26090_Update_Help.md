---
title: "Update Help"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by evman on 2005-04-11
Ok, I've recently installed Hoary Preview (downloaded it about 3 hours before the full release came out :? ) and I've been trying to install some stuff but every time I use apt-get install in the console it tells me that certain dependencies haven't been installed, these are:

xpdf-utils
xscreensaver
xscreensaver-gl
yelp
zenity
zip

It asks me if I want to install them and I say yes, but then it asks for me to put the CD in. The reason those packages were not installed initially is because there's something wrong with my CD and it didn't let them install. I think I need to change where Ubuntu looks for these packages but I'm not sure how to. Any help would be greatly appreciated.

Thanks

---

### Post by whitehat on 2005-04-11
Check your /etc/apt/sources.list for:
```

 ## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

```

This is the standard package update source, however it may be a good idea to do a fresh install with a fully released Hoary.

---

