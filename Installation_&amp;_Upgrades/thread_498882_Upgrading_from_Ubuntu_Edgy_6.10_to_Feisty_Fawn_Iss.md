---
title: "Upgrading from Ubuntu Edgy 6.10 to Feisty Fawn Issues"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by DrFugly on 2007-07-11
So i'm trying to upgrade to Feisty Fawn  7.04 using the Synaptic Package Manager. During the  "Prepare the upgrade" stage I keep getting an error when it attempts to fetch the 95th file. This is the error that I'm getting:

> Failed to fetch [http://beryl-mirror.lupine.me.uk/dists/edgy/Release.gpg](http://beryl-mirror.lupine.me.uk/dists/edgy/Release.gpg) Could not resolve 'beryl-mirror.lupine.me.uk'
Failed to fetch [http://beryl-mirror.lupine.me.uk/dists/edgy/main/i18n/Translation-en_US.bz2](http://beryl-mirror.lupine.me.uk/dists/edgy/main/i18n/Translation-en_US.bz2) Could not resolve 'beryl-mirror.lupine.me.uk'
Failed to fetch [http://givre.cabspace.com/ubuntu/dists/edgy/Release.gpg](http://givre.cabspace.com/ubuntu/dists/edgy/Release.gpg) Could not connect to givre.cabspace.com:80 (65.175.85.100), connection timed out
Failed to fetch [http://givre.cabspace.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://givre.cabspace.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2) Could not connect to givre.cabspace.com:80 (65.175.85.100), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release](http://archive.ubuntu.com/ubuntu/dists/dapper/Release) Unable to find expected entry  mult/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://beryl-mirror.lupine.me.uk/dists/edgy/main/binary-i386/Packages.gz](http://beryl-mirror.lupine.me.uk/dists/edgy/main/binary-i386/Packages.gz) Could not resolve 'beryl-mirror.lupine.me.uk'
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found

Thanks ahead!!!

---

### Post by avik on 2007-07-11
Change everything in your /etc/apt/sources.list that says edgy to feisty:

```
sudo gedit /etc/apt/sources.list
```

---

### Post by DrFugly on 2007-07-11
You mean like just do a search and replace? or only for certain areas (I'm a noob if you haven't noticed)

edit: ok i did a replace but it still doesn't work... any other ideas?

---

### Post by zvacet on 2007-07-12
```
sudo gedit /etc/apt/sources.list
```

Comment all unoffical repos(put #sign in front of line) including one in your post.After that do the upgrade.When it is finish 

```
sudo gedit /etc/apt/sources.list
```

and remove # sign from lines you comment before.After that

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by DrFugly on 2007-07-12
ok silly question... how would i know which ones are official?

edit: ok i think i got that part figured out i just have 1 final issue

> 
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/Release](http://archive.ubuntu.com/ubuntu/dists/feisty/Release)
Unable to find expected entry  mult/binary-i386/Packages in Meta-index
file (malformed Release file?)


don't i need that? Isn't that official?

---

### Post by DrFugly on 2007-07-12
i'm sorry for double posting but this is really bugging me....
Im using an amd x2 3800+ if that helps any... please any ideas on what's going on?

---

### Post by avik on 2007-07-14
> **DrFugly said:**
> i'm sorry for double posting but this is really bugging me....
Im using an amd x2 3800+ if that helps any... please any ideas on what's going on?

Well, your processor is a 64 bit processor, but if you were using Edgy fine, I'm guessing you were running the 32 bit version of Ubuntu.  That doesn't really matter though.

According to [this guide]("http://www.getautomatix.com/wiki/index.php?title=Sources.list"), the official Ubuntu repos are:

```

# Feisty Final Release Repository
deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse

# Feisty Security Updates
deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

# Feisty Bugfix Updates
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse

# Feisty Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

# Ubuntu Commercial
deb http://archive.canonical.com/ubuntu feisty-commercial main
#deb-src http://archive.canonical.com/ubuntu feisty-commercial main

```

Try backing up your sources.list and replacing it with this.  Then try updating via apt-get or aptitude.

---

