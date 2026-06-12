---
title: "Upgrades incomplete"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by arvevans on 2012-11-29
Not all upgrades being upgraded:
[INDENT]
arv@arv-desktop:~$ sudo apt-get update
:
:
:
W: Failed to fetch [http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
arv@arv-desktop:~$ 
[/INDENT]

Problem looks to be an added space prior to "quantel" in the database.

---

### Post by arpanaut on 2012-11-29
From what I can see neither of those PPA;s have quantal packages in them.
Sometimes the previous releases packages work okay, sometimes not.

---

### Post by arvevans on 2012-12-05
I guess I have 2 questions regarding this:
[LIST=1]
[*]What caused these errors which showed up during a routine "apt-get update"?
[*]What should I do to make "apt-get update" work without throwing these errors?
[/LIST]

Thanks,

Arv
_._

---

### Post by arpanaut on 2012-12-05
Apt always checks your /etc/apt/sources.list and what is in /etc/apt/sources.list.d on the update command, if there are erroneous entries there it will report them.  The command sudo apt-get update just updates the available packages for upgrading. The command sudo apt-get upgrade actually does the upgrade, sudo apt-get dist-upgrade may be needed if there is a version change of the available packages.
see "man apt-get"

To stop this error you will need to correct the entries for those ppa's which are probably in your sources.list.d directory. You can do this by hand or use the Software Sources GUI to disable those repositories, they would be under "Other Software" there.

Edit: You might also want to change the quantal to precise in those entries and see if the previous releases packages will work, usually do, sometimes not. Your choice on the risks.

---

### Post by arvevans on 2012-12-06
Okay...that explains what can be done to resolve the problem...but what caused it in the first place?  This occurred shortly after upgrading from 12.04 to 12.10, probably the first time I used apt-get update then apt-get upgrade after the distro upgrade to 12.10.  It looks like something was erroneously retained during the distro upgrade process...?

Later today I will try editing the sources list to clean it up as you recommended.  I will post the results.

Thanks

---

### Post by arpanaut on 2012-12-06
Usually the release upgrade disables PPA's, so yes this is strange.  
Depending on how important those ppa's are to you, you could investigate the usage of previous versions of those ppa's.
Hopefully removing won't glitch up any dependencies, if it does you could try ppa-purge.

---

