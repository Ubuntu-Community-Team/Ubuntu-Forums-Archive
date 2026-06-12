---
title: "install Qt &amp; VTK"
date: 2013-09-24
forum: Installation &amp; Upgrades
---

### Post by maryam2 on 2013-09-24
I am new on ubuntu.
I want to install VTK 5.10 and Qt 4.6 on ubuntu and use from this command:
sudo apt-get install libqt4-dev libvtk5-qt4-dev
unfortunately,at the end of install process it is appeared:
unable to fetch some archives maby run apt-get update or try --fix-missing and also something about " IP:91.189.92.202 "
but befor installation I did update command.
How can I solve this problem please?

---

### Post by su:bhatta on 2013-09-24
libqt4-dev installation also needs at least 10-15 dependencies. Did you get a message to install those lib files also?

Please try
```

sudo apt-get update --fix-missing
```

see what that gives you.

---

### Post by oldos2er on 2013-09-24
maryam2, which version of Ubuntu are you running?

---

### Post by maryam2 on 2013-09-25
hello 
I have ubuntu 12.4
I install ubuntu again and found that I have the same problem when I update with sudo apt-get update command
this was like: Err [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal-updates/main perl i386 5.14.2-13ubuntu0.2
  Connection failed [IP: 91.189.92.200 80]

therefore to solve the problem  I edited "IPV4 Settings" tab and changed the "Method" to "Automatic (DHCP) addresses only". Then, for DNS servers, added "8.8.8.8, 8.8.4.4". and saved and reconnected
then I update again but it is appeared:
ldconfig deferred processing now taking place
Fetched 58.0 MB in 1h 49min 3s (8,865 B/s)

I dont know the meaning of this text 
anyway I installed qt nad vtk again with this command:
sudo apt-get install libqt4-dev libvtk5-qt4-dev 

but I get this txt again:
Failed to fetch [http://ir.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-kb/x11proto-kb-dev_1.0.6-2_all.deb](http://ir.archive.ubuntu.com/ubuntu/pool/main/x/x11proto-kb/x11proto-kb-dev_1.0.6-2_all.deb)  Connection failed [IP: 91.189.92.200 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

in this section I did your advice, dear friend. I try 
sudo apt-get update --fix-missing

and the result was like that(at the end of the result)
Setting up libvtk5.8-qt4 (5.8.0-13build1) ...
Setting up libvtk5-qt4-dev (5.8.0-13build1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

What does it mean? is it good?
HOW CAN I SOLVE THE PROBLEM PLEASE?

---

### Post by oldos2er on 2013-09-25
Quantal is 12.10, not 12.04, so I'm a little confused why you would have that in your sources. Can you copy & paste the output from these commands here, inside code tags? ```
lsb_release -ir

cat /etc/apt/sources.list

ls /etc/apt/sources.list.d/
```

---

### Post by maryam2 on 2013-09-26
[lsb_release -ir
Distributor ID:    Ubuntu
Release:    12.10]

[cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main]

[ls /etc/apt/sources.list.d/
otb-orfeotoolbox-stable-ubuntugis-quantal.list
ubuntugis-ubuntugis-unstable-quantal.list
ubuntugis-ubuntugis-unstable-quantal.list.save]

thank you

---

### Post by oldos2er on 2013-09-26
I'm not familiar with the PPAs you use, but that all looks ok. You're using 12.10, there's no evidence of 12.04.

You could try changing to the main server. In Software Center, click Edit, Software Sources, Download from, change to main server.

---

### Post by maryam2 on 2013-09-26
Thank  you very much. I did what you said and got this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt4-dev is already the newest version.
libvtk5-qt4-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Excuse me as I said before I am new on ubuntu and I don't understand the meaning of something on it.
I want to install special software on ubuntu. but, this software release on a number of other open source software to successfully build.
QT VERSION>4.6
GDAL
Orfeo toolbox
VTK 5.10
how can I install these open source software on ubuntu?
Is it necesssary to download them from internet before installation? 
or I should only use special command for installing each of them?

I worked on windows and I can't understand the meaning of repository on ubuntu for example 
what is the meaning of "Adding launchpad repository"? why should we do that work I mean "Adding repository"?

It is kind of you if you help me please.
Thanks alot

---

### Post by oldos2er on 2013-09-26
A repository is a server containing software that can be installed on an Ubuntu system. If you look at the file /etc/apt/sources.list ```
cat /etc/apt/sources.list
``` you see a list of URLs. Those are repositories. See [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) and [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

A PPA is a repository maintained by private individuals, they're explained in the link above.

If you need help on compiling software, I suggest you start a new thread in [this subforum]("http://ubuntuforums.org/forumdisplay.php?f=44"), giving full details about the software you're working with. Compiling and installing software from source code is not as straightforward as installing software from the repositories.

More info: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

