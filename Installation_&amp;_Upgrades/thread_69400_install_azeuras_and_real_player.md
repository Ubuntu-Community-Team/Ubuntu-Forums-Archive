---
title: "install azeuras and real player"
date: 2005-09-26
forum: Installation &amp; Upgrades
---

### Post by wolf202 on 2005-09-26
Ok so i'm realtivley new to linux, i've used slax and debian before, but ubuntu is by far the best I've tried.  I've followed the instructions in the wiki for installing Real Player and Azeurus but when I use the apt-get command, i get this 


> matthew@ubuntu:~$ sudo apt-get install realplayer
Password:
Reading package lists... Done
Building dependency tree... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package realplayer has no installation candidate


Is there another way i can install these programs?

-wolf

---

### Post by manicka on 2005-09-26
Realplayer

[http://www.ubuntuforums.org/showpost.php?p=369989&postcount=3](http://www.ubuntuforums.org/showpost.php?p=369989&postcount=3)

---

### Post by bored2k on 2005-09-26
Why are you using Nerim? That is for Debian, not UBuntu. Follow our method: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by wolf202 on 2005-09-26
ok i added the nerin for the dvd playback plugins i removed now i get

> matthew@ubuntu:~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate


---

