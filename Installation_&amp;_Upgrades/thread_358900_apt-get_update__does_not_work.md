---
title: "apt-get update  does not work"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by almos on 2007-02-11
Hello,
I have the following problem:

# apt-get update
Get: 1 http://archive.ubuntu.com edgy Release.gpg [191B]
Ign http://archive.ubuntu.com edgy/main Translation-en_GB
Ign http://archive.ubuntu.com edgy/restricted Translation-en_GB
Ign http://archive.ubuntu.com edgy/universe Translation-en_GB
Get: 2 http://archive.ubuntu.com edgy-backports Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_GB
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_GB
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_GB
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_GB
Hit http://archive.ubuntu.com edgy Release
Hit http://archive.ubuntu.com edgy-backports Release
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy-backports/main Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Fetched 2B in 2s (1B/s)
Segmentation faultsts... 0%
#

The root file system is clean.
I tried to remove the unneeded repositories from /etc/apt/sources.list
so it looks like:
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

Any help would be greatly appreciated.

Regards, A.

---

### Post by Macchi on 2007-02-12
Hello almos,
Sorry but I did not understand your problem. If you have a working network connection to the internet, just running "sudo apt-get update" will only resynchronize the package index with the sources, it will not install the latest software packages on your system. 

The actual commands to upgrade from a command-line on the terminal are: 
```
sudo apt-get update
sudo apt-get upgrade
```

or also combined in only one line with help of "&&" :
```
sudo apt-get update && sudo apt-get upgrade
```

These commands will update the package index and upgrade the packages, thus load, install and (re)configure the latest versions for all software already installed on your system.

You may also use the graphical interface and choose "System->Administratrion->Update Manager".

PS: I hope this was helpful and sorry if I made the wrong assumption about the nature of you technical problem. It is OK to ignore the sources but Don't forget the references to security upgrades on the /etc/apt/sources.list!

---

### Post by halfvolle melk on 2007-02-12
Looks like this:
[http://www.debianhelp.org/node/1972](http://www.debianhelp.org/node/1972)
Solution is provided in the link.

Ps. I'd restore the sources.list if I were you as it's not causing the problem. Make sure to at least add the repo's for security updates.

---

### Post by almos on 2007-02-12
Thanks for your help.

apt-get update did segfaults becasue those /var/cache/apt/*.bin files were stale or damaged somehow.

Deleting them, as you suggested, solved my problem.

Regards,
A.

---

