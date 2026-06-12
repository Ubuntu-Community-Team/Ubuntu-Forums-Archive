---
title: "Cannot properly upgrade / install libc6"
date: 2013-11-02
forum: Installation &amp; Upgrades
---

### Post by kyutums on 2013-11-02
I am running Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-54-generic i686) and access it remotely via terminal. During a routine "apt-get upgrade", I started getting errors about libc6.
> thisisme@mycomputer:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.15-0ubuntu10.5) but 2.15-0ubuntu10.4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I tried 'apt-get -f install', but got the following error:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc-bin
1 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1,133 kB of archives.
After this operation, 5,120 B of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libc6

I also tried
> sudo apt-get update
sudo apt-get clean
sudo apt-get install -fy
It seemed to run okay, but encountered the following error:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc-bin
1 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
3 not fully installed or removed.
Need to get 1,133 kB of archives.
After this operation, 5,120 B of additional disk space will be used.
Get:1 [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) precise-updates/main libc-bin i386 2.15-0ubuntu10.5 [1,133 kB]
Fetched 1,133 kB in 5s (202 kB/s)   
E: Internal Error, No file name for libc6

Has anyone experienced this before and resolved it?

---

### Post by kyutums on 2013-11-02
Seems to have been solved. I used the following commands from [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/983543/comments/5](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/983543/comments/5)
> dpkg -i /var/cache/apt/archives/*.deb
dpkg --configure -a

---

