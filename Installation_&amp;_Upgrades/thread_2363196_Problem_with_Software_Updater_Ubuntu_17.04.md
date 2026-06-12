---
title: "Problem with Software Updater Ubuntu 17.04"
date: 2017-06-07
forum: Installation &amp; Upgrades
---

### Post by pepsiman96 on 2017-06-07
Hello everyone!

I just installed Ubuntu 17.04 after having been a Windows man and I'm enjoying it a lot, however I have had a problem with the Software Updater after adding the Bumblebee program because I thought I needed it, as my computer is a ASUS N55SF notebook with Nvidia Optimus. I have seen many people here on the forum already having experienced similar problems with PPAs messing up the Software Updater. The problem is that whenever I try to run a software update session, I get a message saying "Failed to download repository information. Check your internet connection", even though my internet connection works fine nonetheless everywhere else. I have been trying to run a update process in the terminal but the result is the following (the update fails):

```
Ign:1 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty InRelease
Ign:2 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty Release           
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty InRelease                         
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates InRelease [89,2 kB]       
Ign:5 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 Packages
Hit:6 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                           
Ign:7 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all Packages 
Ign:8 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main i386 Packages
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports InRelease [89,2 kB]
Ign:10 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en
Ign:11 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en_US
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security InRelease [89,2 kB]
Ign:13 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all DEP-11 Metadata
Ign:15 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main DEP-11 64x64 Icons
Ign:5 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 Packages
Ign:7 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all Packages
Ign:8 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main i386 Packages
Ign:10 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en
Ign:11 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en_US
Ign:13 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all DEP-11 Metadata
Ign:15 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main DEP-11 64x64 Icons
Ign:5 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 Packages
Ign:7 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all Packages
Ign:8 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main i386 Packages
Ign:10 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en
Ign:11 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en_US
Ign:13 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all DEP-11 Metadata
Ign:15 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main DEP-11 64x64 Icons
Ign:5 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 Packages
Ign:7 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all Packages
Ign:8 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main i386 Packages
Ign:10 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en
Ign:11 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en_US
Ign:13 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all DEP-11 Metadata
Ign:15 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main DEP-11 64x64 Icons
Ign:5 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 Packages
Ign:7 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all Packages
Ign:8 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main i386 Packages
Ign:10 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en
Ign:11 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en_US
Ign:13 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all DEP-11 Metadata
Ign:15 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main DEP-11 64x64 Icons
Err:5 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 Packages
  404  Not Found
Ign:7 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all Packages
Ign:8 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main i386 Packages
Ign:10 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en
Ign:11 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main Translation-en_US
Ign:13 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main all DEP-11 Metadata
Ign:15 [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) zesty/main DEP-11 64x64 Icons
Fetched 268 kB in 2s (120 kB/s)
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/bumblebee/stable/ubuntu zesty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/bumblebee/stable/ubuntu/dists/zesty/main/binary-amd64/Packages](http://ppa.launchpad.net/bumblebee/stable/ubuntu/dists/zesty/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
```


I figured out after a little research that I should remove this PPA, as I later found out you could also just easily get a Nvidia prorpietary driver that easily lets you switch between the graphics card and the Intel integrated one. So I have been trying to run PPA Purge and it did not remove the PPA at all, I'm still getting that annoying error. Cannot do any changes in Software & Updates either as I also there get a error message, so it almost looks like I may have corrupted the updater somehow. This is driving me nuts!

Does anyone here have a solution to the problem that does not require reinstalling Ubuntu, or is that the only option?

Thanks in advance!

---

### Post by pepsiman96 on 2017-06-07
Hi again!

Don't worry! I fixed the problem now, just disabled the PPA and now it works again.

---

### Post by mörgæs on 2017-06-07
Good, please mark the thread 'solved'.

---

