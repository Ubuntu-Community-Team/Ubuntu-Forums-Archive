---
title: "Upgrade/update - connection issue"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by kiddd_ on 2013-02-22
Hello ! I'm stuck on some problems I've been trying to solve these days and I cant' seem to get anywhere with them.First of all I must say that my problem isn't new - however - none of the solutions I've seen on other posts solved my problem/s - and I've read a lot !

I'll try my best in order to explain this the right way. I can't update / upgrade and mainly whatever I try to do ends up with an error which says that I must check my Internet connection.

i.e this is what i get when i try to sudo apt-get update:

root@kiddd-VGN-FW56M:/home/kiddd/Desktop# apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
Ign [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/) maverick/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


I'm running ubuntu 10.10 and I've been trying to upgrade my verion to the last one 12.10. I've tried it with burned dvds ( 11.04 -> 11.10 -> 12.04 -> 12.10 ) and via internet also - no luck.

Please help me out as I am running out of ideas. 

I could backup all the stuff and format/clean install but I really want to FIX this issue. Thank you all for your time !

---

### Post by arpanaut on 2013-02-22
Maverick has reached End of Life, Please see:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by kiddd_ on 2013-02-23
Hello and thank you for your reply !

Same issue strikes again :


The program 'aptitude' can be found in the following packages:
 * aptitude
 * aptitude-gtk
Try: apt-get install <selected package>
root@kiddd-VGN-FW56M:/etc/apt# apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package aptitude is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'aptitude' has no installation candidate
root@kiddd-VGN-FW56M:/etc/apt#

---

