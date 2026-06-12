---
title: "MP3 on XMMS"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by igrachev on 2006-08-10
Hello i installed xmms player from the repository as it is said on this site [http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Player_.28XMMS.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Player_.28XMMS.29) but when i tryed to make the operations with the defaults.list fail i noticed that i have no such file at /usr/share/applications so i made a new empty one and execute the operations said in the side but i still cant play mp3 files what am i supposed to do to be able to play my mp3s ?

PS:Sorry for my bad english but it is my third language and i am not so good in it i hope you have understood me :D. Thanks for helping.

---

### Post by Jagot on 2006-08-10
Have you done this:

[https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59](https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59)

You could also try installing xmms-mad.

---

### Post by igrachev on 2006-08-10
well i havent install any of these libxine-extracodecs or the others but i dont know why when i try to install them it said that "E: Package libxine-extracodecs has no installation candidate" I think this is couse i try to instll plugin for player i dont have but at that list there is no plugins suporting mp3 on xmms but thanks anyway i understood my problem now and will try to find that missing plugins ty

---

### Post by Jagot on 2006-08-10
You need to enable extra repositories as the restricted formats wiki advises you:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

or

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by igrachev on 2006-08-10
well i added 
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free 

to my source.list file but i still dont understand how am i suppose to install these plugins 
when i try this sudo apt-get install libxine-extracodecs it again say that there is no installation candidate ... i am not sure but i think that with this comand i am trying to install mp3 plugins for K3b whitch must be a player i dont know .... :(

---

