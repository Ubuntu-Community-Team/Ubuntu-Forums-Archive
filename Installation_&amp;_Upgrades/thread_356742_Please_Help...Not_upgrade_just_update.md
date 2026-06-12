---
title: "Please Help...Not upgrade just update"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by magichsjx on 2007-02-08
[B]hello
I am running a Dapper LiveCD 6.0.6 LTS and here's my problem ( I got 3 sofar trying sources lists and so on). I installed a package that removes orphans and i thought it was cool its called (something)orphan as i was told on psychocats site and i deleted some packages when i tried it again i would hope the slate was clean, well low and behold new packages were set to be removed that is where i stopped. I do not remember which packages were removed but i think they had "lib" in their names and likely not essentila ones but anyhow, I must say I had used a new sources list from someone on here not knowing you could use the update manager to update your list, which was also on psychocats so i felt it was a good one but after that i got this icon on the top right reminding me of the updates and so on. its rather bulky 160 MB and i m on linux dialup so i havent done it yet (at 1446 kb/sec would take 30 odd hours). Now after the orphan thing I get these errors when i go to install or attempt to install the updates when the kernel was mentioned i was scared cause that's touchy. anyhow heer are the errors i get when trying to update:

> The following problems were found on your system:

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)


> Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.


The following updates will be skipped:

linux-image-386
linux-restricted-modules-386

> The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[ftp://archive.ubuntu.com/ubuntu/dists/dapper/Release:](ftp://archive.ubuntu.com/ubuntu/dists/dapper/Release:) Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)

> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.



[ftp://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](ftp://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Temporary failure resolving 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Temporary failure resolving 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Temporary failure resolving 'archive.ubuntu.com'
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Temporary failure resolving 'security.ubuntu.com'
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg:) Temporary failure resolving 'archive.canonical.com'
[http://www.getautomatix.com/apt/dists/dapper/Release.gpg:](http://www.getautomatix.com/apt/dists/dapper/Release.gpg:) Temporary failure resolving 'www.getautomatix.com'
[http://archive.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Temporary failure resolving 'archive.ubuntu.com'
[http://people.ubuntu.com/~seb128/deb/./Release.gpg:](http://people.ubuntu.com/~seb128/deb/./Release.gpg:) Temporary failure resolving 'people.ubuntu.com'
[http://theli.free.fr/packages/dists/dapper/Release.gpg:](http://theli.free.fr/packages/dists/dapper/Release.gpg:) Temporary failure resolving 'theli.free.fr'
[http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg:](http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg:) Temporary failure resolving 'wine.lowvoice.nl'
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Temporary failure resolving 'archive.ubuntu.com'
[http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg:](http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg:) Temporary failure resolving 'wine.budgetdedicated.com'


If anyone can tell me how i should go about updating my kernel and packages and what not I would be extremely grateful.
cheers!![/B]

---

### Post by loserboy on 2007-02-08
[http://ubuntuforums.org/showthread.php?t=356408](http://ubuntuforums.org/showthread.php?t=356408)

look at this thread, most likely is your problem

---

### Post by magichsjx on 2007-02-08
tyvm i don't feel so bad now :)

---

