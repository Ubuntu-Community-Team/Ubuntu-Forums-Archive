---
title: "QT unmet dependencies when upgrading smplayer"
date: 2016-06-17
forum: Installation &amp; Upgrades
---

### Post by tigerjack89 on 2016-06-17
I was trying to upgrade smplayer, but aptitude tells that it's unable to solve the dependencies for libqt5script5

```

$>sudo aptitude dist-upgrade 
The following NEW packages will be installed:
  libqt5script5{ab} 
The following packages will be upgraded:
  smplayer smtube 
2 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,846 kB of archives. After unpacking 3,191 kB will be used.
The following packages have unmet dependencies:
 libqt5script5 : Depends: qtbase-abi-5-2-1 which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:                       
1)     smplayer                                           
2)     smplayer-skins                                     
3)     smplayer-themes                                    
4)     smtube                                             

     Keep the following packages at their current version:
5)     libqt5script5 [Not Installed] 

```

The libqt5script5 package, however, depends on the qtbase-abi-5-2-1 virtual package, so I can't install it. How can I fix this problem?

---

### Post by tigerjack89 on 2016-06-21
bump

---

### Post by mc4man on 2016-06-21
You should post what release of Ubuntu, what's your current smplayer package version & where are you getting this upgraded smplayer from?
On the face of it it seems you're going from a qt4 smplayer to a qt5 one.

---

### Post by tigerjack89 on 2016-06-21
> **mc4man said:**
> You should post what release of Ubuntu, what's your current smplayer package version & where are you getting this upgraded smplayer from?
On the face of it it seems you're going from a qt4 smplayer to a qt5 one.
I'm on Ubuntu 14.04. About smplayer, this is what it's installed on my system

```
$>dpkg -l | grep smplayer
ii  smplayer                                                    16.4.0-1~trusty1                                    amd64        A great media player
ii  smplayer-skins                                              2:15.2.0-1~trusty1                                  all          Skin themes for SMPlayer
ii  smplayer-themes                                             2:16.6.0-1~trusty1                                  all          Icon themes for SMPlayer

```

while the updates are taken from [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu)


About qt4 and qt5, I've a lot of packages from both, but I can't simply uninstall one of them because they are both used by different packages.
What seeems to be the cause of the problem is the  qtbase-abi-5-2-1 package, that can't be installed at all.

This package should be provided by libqt5core5a, which I have already installed.

---

### Post by mc4man on 2016-06-21
rvm has moved to latest smplayer build for trusty to qt5, there should be no issue upgrading or installing. 
I no longer use aptitude much so don't don't really get what it's wanting to do. Maybe just try, assumes you have the [smplayer ppa]("https://launchpad.net/~rvm/+archive/ubuntu/smplayer") enabled - 

```
sudo apt-get install --only-upgrade smplayer smtube smplayer-themes
```

works fine here, ex.

> ~$ sudo apt-get install --only-upgrade smplayer smtube smplayer-themes
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libqt5script5
The following NEW packages will be installed:
  libqt5script5
The following packages will be upgraded:
  smplayer smplayer-themes smtube
3 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 6,635 kB of archives.
After this operation, 3,912 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main libqt5script5 amd64 5.2.1+dfsg-1ubuntu1 [691 kB]
Get:2 [http://ppa.launchpad.net/rvm/smplayer/ubuntu/](http://ppa.launchpad.net/rvm/smplayer/ubuntu/) trusty/main smplayer amd64 16.6.0-1~trusty1 [2,853 kB]
Get:3 [http://ppa.launchpad.net/rvm/smplayer/ubuntu/](http://ppa.launchpad.net/rvm/smplayer/ubuntu/) trusty/main smplayer-themes all 2:16.6.0-1~trusty1 [2,789 kB]
Get:4 [http://ppa.launchpad.net/rvm/smplayer/ubuntu/](http://ppa.launchpad.net/rvm/smplayer/ubuntu/) trusty/main smtube amd64 16.6.0-1~trusty1 [303 kB]
Fetched 6,635 kB in 5s (1,239 kB/s)
Selecting previously unselected package libqt5script5:amd64.
(Reading database ... 262697 files and directories currently installed.)
Preparing to unpack .../libqt5script5_5.2.1+dfsg-1ubuntu1_amd64.deb ...
Unpacking libqt5script5:amd64 (5.2.1+dfsg-1ubuntu1) ...
Preparing to unpack .../smplayer_16.6.0-1~trusty1_amd64.deb ...
Unpacking smplayer (16.6.0-1~trusty1) over (16.1.0-1~trusty1) ...
Preparing to unpack .../smplayer-themes_2%3a16.6.0-1~trusty1_all.deb ...
Unpacking smplayer-themes (2:16.6.0-1~trusty1) over (2:15.12.0-1~trusty1) ...
Preparing to unpack .../smtube_16.6.0-1~trusty1_amd64.deb ...
Unpacking smtube (16.6.0-1~trusty1) over (16.3.0-1~trusty1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libqt5script5:amd64 (5.2.1+dfsg-1ubuntu1) ...
Setting up smplayer (16.6.0-1~trusty1) ...
Setting up smplayer-themes (2:16.6.0-1~trusty1) ...
Setting up smtube (16.6.0-1~trusty1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...

---

### Post by tigerjack89 on 2016-06-22
> **mc4man said:**
> rvm has moved to latest smplayer build for trusty to qt5, there should be no issue upgrading or installing. 
I no longer use aptitude much so don't don't really get what it's wanting to do. Maybe just try, assumes you have the [smplayer ppa]("https://launchpad.net/~rvm/+archive/ubuntu/smplayer") enabled - 

```
sudo apt-get install --only-upgrade smplayer smtube smplayer-themes
```

works fine here, ex.

With the same ppa, using apt-get instead of aptitude and the --only-upgrade option

```

$>sudo apt-get install --only-upgrade smplayer smtube smplayer-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smplayer-themes is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 smplayer : Depends: libqt5script5 (>= 5.0.2) but it is not going to be installed
 smtube : Depends: libqt5script5 (>= 5.0.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by mc4man on 2016-06-22
Then look at libqt5script5 & see what's blocking install. You could start with 
```
apt-cache policy libqt5core5a libqt5script5
```

Ex. here
```
$ apt-cache policy libqt5core5a libqt5script5
libqt5core5a:
  Installed: 5.2.1+dfsg-1ubuntu14.3
  Candidate: 5.2.1+dfsg-1ubuntu14.3
  Version table:
 *** 5.2.1+dfsg-1ubuntu14.3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.2.1+dfsg-1ubuntu14 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
libqt5script5:
  Installed: 5.2.1+dfsg-1ubuntu1
  Candidate: 5.2.1+dfsg-1ubuntu1
  Version table:
 *** 5.2.1+dfsg-1ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by tigerjack89 on 2016-06-22
> **mc4man said:**
> Then look at libqt5script5 & see what's blocking install. You could start with 

As I said in the OP
> **tigerjack89 said:**
> 
The libqt5script5 package, however, depends on the qtbase-abi-5-2-1 virtual package, so I can't install it. How can I fix this problem?

This is the culprit, but I don't know why.
Btw, here the output of your command

```

$> apt-cache policy libqt5core5a libqt5script5
libqt5core5a:
  Installed: 5.3.0+dfsg-2ubuntu9~trusty1
  Candidate: 5.3.0+dfsg-2ubuntu9~trusty1
  Version table:
 *** 5.3.0+dfsg-2ubuntu9~trusty1 0
        100 /var/lib/dpkg/status
     5.2.1+dfsg-1ubuntu14.3 0
        500 http://ftp.hawo.stw.uni-erlangen.de/ubuntu/ trusty-security/main amd64 Packages
        500 http://ftp.hawo.stw.uni-erlangen.de/ubuntu/ trusty-updates/main amd64 Packages
     5.2.1+dfsg-1ubuntu14 0
        500 http://ftp.hawo.stw.uni-erlangen.de/ubuntu/ trusty/main amd64 Packages
libqt5script5:
  Installed: (none)
  Candidate: 5.2.1+dfsg-1ubuntu1
  Version table:
     5.2.1+dfsg-1ubuntu1 0
        500 http://ftp.hawo.stw.uni-erlangen.de/ubuntu/ trusty/main amd64 Packages

```

---

### Post by mc4man on 2016-06-22
Pretty simple why - 
You've used this ppa which has given you a version/abi of some qt5 libs higher than what's in 14.04.
[https://launchpad.net/~mscore-ubuntu/+archive/ubuntu/mscore-stable](https://launchpad.net/~mscore-ubuntu/+archive/ubuntu/mscore-stable)

So live with what that ppa breaks inc. not being able to upgrade smplayer or get rid of all the packages it provided & replace with the Ubuntu 14.04 versions. 
You may be able to use ppa-purge to do this or due to current state of the ppa it may not work.
(that ppa is a joke...

---

### Post by tigerjack89 on 2016-06-22
> **mc4man said:**
> Pretty simple why - 
You've used this ppa which has given you a version/abi of some qt5 libs higher than what's in 14.04.
[https://launchpad.net/~mscore-ubuntu/+archive/ubuntu/mscore-stable](https://launchpad.net/~mscore-ubuntu/+archive/ubuntu/mscore-stable)

So live with what that ppa breaks inc. not being able to upgrade smplayer or get rid of all the packages it provided & replace with the Ubuntu 14.04 versions. 
You may be able to use ppa-purge to do this or due to current state of the ppa it may not work.
(that ppa is a joke...
Mmm, I´m not sure I got you. What kind of packages are you talking of?

---

### Post by mc4man on 2016-06-22
> **tigerjack89 said:**
> Mmm, I´m not sure I got you. What kind of packages are you talking of?

Well for starters the root of your issues - libqt5core5a
> apt-cache policy libqt5core5a libqt5script5
libqt5core5a:
  Installed: 5.3.0+dfsg-2ubuntu9~trusty1
  Candidate: 5.3.0+dfsg-2ubuntu9~trusty1
That is from the ppa & is qtbase-abi-5-3-0

---

### Post by tigerjack89 on 2016-06-24
> **mc4man said:**
> Well for starters the root of your issues - libqt5core5a

That is from the ppa & is qtbase-abi-5-3-0
So, what should I do in your opinion? I don't know which ppa installed the latest libqt5core5a version.

---

