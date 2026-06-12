---
title: "apt-get update giving error- no download from software center or terminal"
date: 2011-12-06
forum: Installation &amp; Upgrades
---

### Post by pavi_elex on 2011-12-06
I have installed new Ubuntu 11.04 from .iso file but when I try to run 
sudo apt-get update
It gives me following error. 
Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/main/source/Sources)  404 not found [IP: 81.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/universe/binary-i386/Packages) 404 not found [IP: 81.189.88.40 80]
Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/multiverse/binary-i386/Packages)  404 not found [IP: 81.189.88.40 80]
Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/restricted/binary-i386/Packages)  404 not found [IP: 81.189.88.40 80]
Failed to fetch  [http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/natty-proposed/main/binary-i386/Packages)  404 not found [IP: 81.189.88.40 80]


I have tried all these but it does not solve my problem.I am still facing errors.

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
 sudo dpkg --clear-avail
 sudo dpkg --configure -a
 sudo apt-get clean
 sudo apt-get update

My internet connection is perfect. I am able to open all sites.
I am not able to download any software from Ubuntu-software center.
It shows error - "Failed to download repository information"
I am not able to install software using terminal by install command.
It shows error - "Unable to locate Package"
Synaptic package manager is not able to fix broken packages because the "apply" button is disabled and mark for installation or re-installation is also disabled.It is not able to download new package information neither repository.
It shows "Could not download all repository indexes"

Please solve my problem.

---

### Post by zvacet on 2011-12-06
In s**ynaptic>repositories** change server and see if that help.are you behind proxy?

---

