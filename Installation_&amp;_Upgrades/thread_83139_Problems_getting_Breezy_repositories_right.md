---
title: "Problems getting Breezy repositories right"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by CalleKubuntu on 2005-10-28
Friends

I downloaded the Kubuntu and burnded a CD, which I then used to upgrade my  Kubuntu from Hoary to Breezy. That went mostly well, and I have a working system. The one main problem I still have is that I cannot get any repositories to work in the /etc/apt/sources.list

I work in China, so I tried to find local Breezy repostiories and found the following:

[http://archive.ubuntu.org.cn/ubuntu/dists/breezy/](http://archive.ubuntu.org.cn/ubuntu/dists/breezy/)
and
[http://cn.archive.ubuntu.com/ubuntu/dists/breezy/](http://cn.archive.ubuntu.com/ubuntu/dists/breezy/)

Well, but then I could not figure out the correct way to put that into the sources.list. 
I tried various ways, but always I got an error message. Think it was about the same error I got later (see below). 

Then I copied the exact lines from user Invalid at [http://ubuntuforums.org/showthread.php?t=74001](http://ubuntuforums.org/showthread.php?t=74001)

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
....

But, again I get these errors below, when starting Synaptic:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

How can I get the sources.list set up properly to use Repositories? I cannot get it to work with any of the Breezy Repositories.

Please give me some good advice, will you.

Thanks
CalleKubuntu

---

### Post by Emerzen on 2005-10-28
##Here's my list:

# Example sources.list for Ubuntu 5.10 "The Breezy Badger" release

## All officially supported packages, including security- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## The source pacakges
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## All community supported packages, including security- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse

## The source pacakges
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse

##Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

## PLF Repo's
#deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
#deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

##Wine Repo's
deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
deb-src [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/

##Note that the "us" in the url's has been removed.

---

### Post by CalleKubuntu on 2005-10-28
Friends

I solved the problem. I just went into the Synaptic, ignoring the errors below:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_bin ary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restrict ed_binary-i386_Packages) - stat (2 No such file or directory)

And then I did a Reload, and it found the site!

I only get one error which is something like:
"The following one could not be found. It could be outdated or ..."
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz:) Sub-process gzip returned an error code (1)

I think I can actually again try the Chinese repositories and see how it goes.

Thanks
CalleKubuntu

---

### Post by aysiu on 2005-10-28
I wouldn't use the Chinese or US repositories. Follow the instructions here:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

This is what happens with me (with those sources): ```
sudo apt-get update
Password:
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:3 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:5 http://archive.ubuntu.com breezy-updates Release [30.9kB]
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Fetched 50.9kB in 1s (28.1kB/s)
Reading package lists... Done

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

