---
title: "apt-get update offline"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by anupam89 on 2010-02-27
I want to update the package index files offline. The command I used to find the list of files to be downloaded is 

#sudo apt-get -qq --print-uris update | awk -F\' ' { print $2}' 

and the output is 

[http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/karmic/Release](http://archive.ubuntu.com/ubuntu/dists/karmic/Release)
[http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)
[http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.bz2)
[http://archive.canonical.com/ubuntu/dists/karmic/partner/source/Sources.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/source/Sources.bz2)
[http://archive.canonical.com/ubuntu/dists/karmic/Release](http://archive.canonical.com/ubuntu/dists/karmic/Release)
[http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg](http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg)
[http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2)

I want to know where should I copy ths files?

---

### Post by khelben1979 on 2010-02-27
I'm not sure exactly what your trying to do, but if you're wondering where the package text file is (for starters) I would try and check out: [PHP]/etc/apt/sources.list[/PHP]

You can edit the sources.list as you wish. If you want to update the file by collecting information from your current sources, I don't see that it's possible because it collects them using your internet connection.

---

### Post by 2hot6ft2 on 2010-02-27
You should check into this for updating an offline ubuntu install
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by codemaniac on 2010-02-27
i think if you dont know how to use command line right stick with the GUI....u can abstain from editing
/etc/apt/sources.lst manually...and add install sources using the GUI...this can teach u a bit of awk   [www.gnu.org/manual/](www.gnu.org/manual/)**gawk**/**gawk**.[B]pdf
 
[/B]

---

### Post by anupam89 on 2010-02-28
What I wanted to know was how to perform 
$sudo apt-get update         
offline. This just updates the package index files. When apt-get update is run what are the files that are modified?

---

### Post by sandy8925 on 2010-03-12
See this link:

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

