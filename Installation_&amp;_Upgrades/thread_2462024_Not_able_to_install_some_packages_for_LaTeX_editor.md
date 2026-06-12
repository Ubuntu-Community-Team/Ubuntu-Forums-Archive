---
title: "Not able to install some packages for LaTeX editor, why ?"
date: 2021-05-12
forum: Installation &amp; Upgrades
---

### Post by priyanshu-gif on 2021-05-12
Hi Experts, 

I am trying to install LaTeX editor but i am getting this...why ? can anyone help me please.
======================================================================================================================================================================================================
```
priyanshu@priyanshu-Inspiron-5593:~$ sudo apt-get install TeXstudio
[sudo] password for priyanshu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package TeXstudio
priyanshu@priyanshu-Inspiron-5593:~$ sudo add-apt-repository ppa:sunderme/texstudio
 Builds for texstudio
 More info: [https://launchpad.net/~sunderme/+archive/ubuntu/texstudio](https://launchpad.net/~sunderme/+archive/ubuntu/texstudio)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal InRelease     
Hit:2 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-updates InRelease
Hit:3 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-backports InRelease
Hit:4 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-security InRelease
Hit:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Get:6 [http://ppa.launchpad.net/sunderme/texstudio/ubuntu](http://ppa.launchpad.net/sunderme/texstudio/ubuntu) focal InRelease [17.5 kB]
Hit:7 [http://ppa.launchpad.net/ubuntudde-dev/stable/ubuntu](http://ppa.launchpad.net/ubuntudde-dev/stable/ubuntu) focal InRelease
Get:8 [http://ppa.launchpad.net/sunderme/texstudio/ubuntu](http://ppa.launchpad.net/sunderme/texstudio/ubuntu) focal/main amd64 Packages [696 B]
Get:9 [http://ppa.launchpad.net/sunderme/texstudio/ubuntu](http://ppa.launchpad.net/sunderme/texstudio/ubuntu) focal/main Translation-en [356 B]
Fetched 18.6 kB in 7s (2,768 B/s)                                              
Reading package lists... Done
priyanshu@priyanshu-Inspiron-5593:~$ sudo apt-get remove texstudio-doc texstudio-l10n
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'texstudio-doc' is not installed, so not removed
Package 'texstudio-l10n' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gstreamer1.0-gtk3 libabw-0.1-1 libboost-date-time1.71.0
  libboost-filesystem1.71.0 libboost-iostreams1.71.0 libboost-locale1.71.0
  libclucene-contribs1v5 libclucene-core1v5 libcmis-0.5-5v5 libcolamd2
  libe-book-0.1-1 libeot0 libepubgen-0.1-1 libetonyek-0.1-1
  libexttextcat-2.0-0 libgpgmepp6 libmhash2 libmwaw-0.3-3 libmythes-1.2-0
  libneon27-gnutls libodfgen-0.1-1 liborcus-0.15-0 libraptor2-0 librasqal3
  librdf0 librevenge-0.0-0 libsuitesparseconfig5 libwpd-0.10-10 libwpg-0.3-3
  libwps-0.4-4 libxmlsec1 libxmlsec1-nss libyajl2 lp-solve
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
priyanshu@priyanshu-Inspiron-5593:~$ sudo apt-get update && sudo apt-get install texstudio
Hit:1 [http://ppa.launchpad.net/sunderme/texstudio/ubuntu](http://ppa.launchpad.net/sunderme/texstudio/ubuntu) focal InRelease
Hit:2 [http://ppa.launchpad.net/ubuntudde-dev/stable/ubuntu](http://ppa.launchpad.net/ubuntudde-dev/stable/ubuntu) focal InRelease
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:4 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal InRelease
Hit:5 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-updates InRelease
Hit:6 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-backports InRelease
Hit:7 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-security InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 texstudio : Depends: libpoppler-qt5-1 (>= 0.81.0) but 0.80.0-0ubuntu4 is to be installed
             Depends: libqt5script5 (>= 5.6.0~beta) but it is not going to be installed
             Recommends: latex-beamer but it is not installable
E: Unable to correct problems, you have held broken packages.
priyanshu@priyanshu-Inspiron-5593:~$ ^C
priyanshu@priyanshu-Inspiron-5593:~$  sudo apt-get install -y libpoppler-qt5-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpoppler-qt5-1 is already the newest version (0.80.0-0ubuntu4).
libpoppler-qt5-1 set to manually installed.
The following packages were automatically installed and are no longer required:
  gstreamer1.0-gtk3 libabw-0.1-1 libboost-date-time1.71.0
  libboost-filesystem1.71.0 libboost-iostreams1.71.0 libboost-locale1.71.0
  libclucene-contribs1v5 libclucene-core1v5 libcmis-0.5-5v5 libcolamd2
  libe-book-0.1-1 libeot0 libepubgen-0.1-1 libetonyek-0.1-1
  libexttextcat-2.0-0 libgpgmepp6 libmhash2 libmwaw-0.3-3 libmythes-1.2-0
  libneon27-gnutls libodfgen-0.1-1 liborcus-0.15-0 libraptor2-0 librasqal3
  librdf0 librevenge-0.0-0 libsuitesparseconfig5 libwpd-0.10-10 libwpg-0.3-3
  libwps-0.4-4 libxmlsec1 libxmlsec1-nss libyajl2 lp-solve
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
priyanshu@priyanshu-Inspiron-5593:~$ sudo apt-get update && sudo apt-get install texstudio
Hit:1 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal InRelease     
Hit:2 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-updates InRelease
Hit:3 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-backports InRelease
Hit:4 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-security InRelease
Hit:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:6 [http://ppa.launchpad.net/sunderme/texstudio/ubuntu](http://ppa.launchpad.net/sunderme/texstudio/ubuntu) focal InRelease
Hit:7 [http://ppa.launchpad.net/ubuntudde-dev/stable/ubuntu](http://ppa.launchpad.net/ubuntudde-dev/stable/ubuntu) focal InRelease
Reading package lists... Done                      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 texstudio : Depends: libpoppler-qt5-1 (>= 0.81.0) but 0.80.0-0ubuntu4 is to be installed
             Depends: libqt5script5 (>= 5.6.0~beta) but it is not going to be installed
             Recommends: latex-beamer but it is not installable
E: Unable to correct problems, you have held broken packages.
priyanshu@priyanshu-Inspiron-5593:~$ sudo apt-get install -y libpoppler-qt5-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpoppler-qt5-1 is already the newest version (0.80.0-0ubuntu4).
The following packages were automatically installed and are no longer required:
  gstreamer1.0-gtk3 libabw-0.1-1 libboost-date-time1.71.0
  libboost-filesystem1.71.0 libboost-iostreams1.71.0 libboost-locale1.71.0
  libclucene-contribs1v5 libclucene-core1v5 libcmis-0.5-5v5 libcolamd2
  libe-book-0.1-1 libeot0 libepubgen-0.1-1 libetonyek-0.1-1
  libexttextcat-2.0-0 libgpgmepp6 libmhash2 libmwaw-0.3-3 libmythes-1.2-0
  libneon27-gnutls libodfgen-0.1-1 liborcus-0.15-0 libraptor2-0 librasqal3
  librdf0 librevenge-0.0-0 libsuitesparseconfig5 libwpd-0.10-10 libwpg-0.3-3
  libwps-0.4-4 libxmlsec1 libxmlsec1-nss libyajl2 lp-solve
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
priyanshu@priyanshu-Inspiron-5593:~$ sudo apt-get install -y libqt5script5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt5script5 : Depends: qtbase-abi-5-12-5
E: Unable to correct problems, you have held broken packages.
priyanshu@priyanshu-Inspiron-5593:~$ sudo apt-get install -y  qtbase-abi-5-12-5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package qtbase-abi-5-12-5 is a virtual package provided by:
  libqt5core5a 5.12.5+dfsg-2 [Not candidate version]

E: Package 'qtbase-abi-5-12-5' has no installation candidate
priyanshu@priyanshu-Inspiron-5593:~$ 
```

---

### Post by Impavidus on 2021-05-12
I don't use texstudio. I use LaTeX, but I prefer to stick to the command line tools. But texstudio is available from the normal repositories. From your output I can see you use Ubuntu 20.04, where you can get texstudio from the universe repository (I don't know if that's enabled by default, else enable it):```
sudo apt install texstudio
```No capital letters, that was wrong in your first command. It will give you version 2.12.22.

If you want a more recent version, you may be able to get it from that PPA. However, it appears that the texstudio from that PPA depends on later versions of some other libraries (like libpoppler) than the versions available on Ubuntu 20.04, so you need a more recent version of those libraries too, maybe from some other PPA. Other tools also rely on those libraries, so may have to be updated too. Welcome to dependency hell.

The best option would be to remove that PPA from your system and simply use the version of texstudio from the standard repositories of Ubuntu 20.04. If you really need a more recent version, you can consider running Ubuntu 21.04, which has texstudio 3.0.4.

Note that texstudio is just the editor and some integration tools. The core components of TeX are in the texlive-base etc. packages, which texstudio depends on. If you wish to upgrade a particular TeX package from the version included in your version of TeXLive, the best way is to manually install the new version in /usr/local/share/texmf.

---

### Post by priyanshu-gif on 2021-05-12
Thanks for your reply!
now i am getting this...
```

priyanshu@priyanshu-Inspiron-5593:~$ sudo apt install texstudio
[sudo] password for priyanshu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 texstudio : Depends: libpoppler-qt5-1 (>= 0.81.0) but 0.80.0-0ubuntu4 is to be installed
             Depends: libqt5script5 (>= 5.6.0~beta) but it is not going to be installed
             Recommends: latex-beamer but it is not installable
E: Unable to correct problems, you have held broken packages.
priyanshu@priyanshu-Inspiron-5593:~$ sudo apt install latex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package latex

```
i already installed Texlive-full, but i am getting trouble in intalling the Latex editors due to these packages.
so can you please help me to install the editor, even i can install Latex too but how can i do that, i am not able to install this. can you please provide any link so i can install Latex editor in a very easy way.
Thanks

---

### Post by Impavidus on 2021-05-12
Do you really need TeXStudio version 3.1.1 or are you happy with version 2.12.22? In the latter case, remove that sunderme/texstudio PPA you added. In the former case, no easy solution.

---

### Post by priyanshu-gif on 2021-05-13
No, not specifically Texstudio....but i want to install any one editor of latex so i can make my documents in that.
it could be anyone that i can install easily.
so can you please suggest me ?

---

### Post by Impavidus on 2021-05-13
So you don't really need TeXstudio 3.1.1? Then you can disable the PPA you added and install TeXstudio 2.12.22 from the repos:```
sudo apt-add-repository --remove ppa:sunderme/texstudio
sudo apt update
sudo apt install texstudio
```If your system is in the state I think it is in, that should work.

If your only intention is to edit LaTeX files and you don't mind using the command line, there's no need for TeXstudio. Every somewhat decent text editor has syntax highlighting for LaTeX built in. In the past I used nedit and gedit to type my LaTeX files. Now I use vim. I've never used an integrated environment for any programming in (La)TeX, C, PostScript, whatever. I like to choose my own favourite editor, compiler, viewer etc. and integrate them in my own way.

Keep in mind, LaTeX is not an editor in which you can type beautiful documents. It's a bunch of command line tools and macro packages that can turn source code into beautiful documents. LaTeX doesn't care how you create your source code files.

---

### Post by priyanshu-gif on 2021-05-13
Thank you so much for your prompt reply!
i just wanted to know that if i am not able to install any package then is it Ubuntu version problem or anything else?
or not version problem, then how can i install other packages and from where ?
like the package libqt5script5 (>= 5.6.0~beta), how can i install this ? below you can see !
```

priyanshu@priyanshu-Inspiron-5593:~$ sudo apt-add-repository --remove ppa:sunderme/texstudio
[sudo] password for priyanshu: 
 Builds for texstudio
 More info: [https://launchpad.net/~sunderme/+archive/ubuntu/texstudio](https://launchpad.net/~sunderme/+archive/ubuntu/texstudio)
Press [ENTER] to continue or Ctrl-c to cancel removing it.

priyanshu@priyanshu-Inspiron-5593:~$ sudo apt update
Hit:1 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal InRelease     
Hit:2 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-updates InRelease
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:4 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-backports InRelease
Hit:5 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal-security InRelease
Hit:6 [http://ppa.launchpad.net/ubuntudde-dev/stable/ubuntu](http://ppa.launchpad.net/ubuntudde-dev/stable/ubuntu) focal InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
priyanshu@priyanshu-Inspiron-5593:~$ sudo apt install texstudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 texstudio : Depends: libqt5script5 (>= 5.6.0~beta) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by QIII on 2021-05-13
First: ***Is this actually Ubuntu, or is this a derivative?***  

Ubuntu version problem?  
Unknown.  What is the release?  Your mirrors appear to be verified, but they aren't the main repos.

You might try to install libqt5script5 (>= 5.6.0~beta) specifically as you attempt to install texstudio.  I see that 5.12.8 is available in *Canonical's* Focal repos.

---

### Post by Impavidus on 2021-05-15
The situation is a bit more complex than appeared on first sight. What version of the different packages concerned have you installed or are available?```
apt-cache policy texstudio libpoppler-qt5-1 libqt5script5
```And to make sure there's nothing wrong with your software sources (and make sure what version of Ubuntu you actually run), also post this:```
cat /etc/apt/sources.list
```

---

### Post by priyanshu-gif on 2021-05-16
Thank you very much for you help!
i run this and getting this...
```
priyanshu@priyanshu-Inspiron-5593:~$ apt-cache policy texstudio libpoppler-qt5-1 libqt5script5
texstudio:
  Installed: (none)
  Candidate: 2.12.16+debian-1.1
  Version table:
     2.12.16+debian-1.1 500
        500 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal/universe amd64 Packages
libpoppler-qt5-1:
  Installed: 0.80.0-0ubuntu4
  Candidate: 0.80.0-0ubuntu4
  Version table:
 *** 0.80.0-0ubuntu4 500
        500 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal/universe amd64 Packages
        100 /var/lib/dpkg/status
libqt5script5:
  Installed: (none)
  Candidate: 5.12.5+dfsg-2
  Version table:
     5.12.5+dfsg-2 500
        500 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal/universe amd64 Packages
```

---

### Post by priyanshu-gif on 2021-05-16
```
priyanshu@priyanshu-Inspiron-5593:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731)]/ focal main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://repos.del.extreme-ix.org/ubuntu/](http://repos.del.extreme-ix.org/ubuntu/) focal main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://repos.del.extreme-ix.org/ubuntu/](http://repos.del.extreme-ix.org/ubuntu/) focal-updates main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://repos.del.extreme-ix.org/ubuntu/](http://repos.del.extreme-ix.org/ubuntu/) focal universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal universe
deb [http://repos.del.extreme-ix.org/ubuntu/](http://repos.del.extreme-ix.org/ubuntu/) focal-updates universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://repos.del.extreme-ix.org/ubuntu/](http://repos.del.extreme-ix.org/ubuntu/) focal multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://repos.del.extreme-ix.org/ubuntu/](http://repos.del.extreme-ix.org/ubuntu/) focal-updates multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://repos.del.extreme-ix.org/ubuntu/](http://repos.del.extreme-ix.org/ubuntu/) focal-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner

deb [http://repos.del.extreme-ix.org/ubuntu/](http://repos.del.extreme-ix.org/ubuntu/) focal-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb [http://repos.del.extreme-ix.org/ubuntu/](http://repos.del.extreme-ix.org/ubuntu/) focal-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://repos.del.extreme-ix.org/ubuntu/](http://repos.del.extreme-ix.org/ubuntu/) focal-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
```

---

### Post by Impavidus on 2021-05-17
Although your software sources appear to be OK and your mirror is on the list of official mirrors, the versions of those packages don't match the versions in the official repositories. It offers:
texstudio 2.12.16+debian-1.1 instead of 2.12.22+debian-1build1;
libpoppler-qt5-1 0.80.0-0ubuntu4 instead of 0.86.1-0ubuntu1;
libqt5script5 5.12.5+dfsg-2 instead of 5.12.8+dfsg-0ubuntu1.
There appears to be something wrong with that mirror.

Can you change to a different mirror or the main server, then run```
sudo apt update
sudo apt upgrade
```

If the problem persists, show again the output of```
apt-cache policy texstudio libpoppler-qt5-1 libqt5script5
apt show texstudio
```

---

### Post by priyanshu-gif on 2021-05-17
so sorry to disturb you but i am not very much comfortable to work in Linux OS.
can you please tell me the  meaning of this 
"Can you change to a different mirror or the main server"
How can i do this ? and will it affect to my other softwares that i have installed in my machine ? 
Thanks
priyanshu

---

### Post by slickymaster on 2021-05-17
@priyanshu-gif:

Please [use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output because if posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of code tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by Impavidus on 2021-05-17
Go to your settings &#8594; Software and Updates &#8594; Ubuntu software, in the dropdown box for "Download from:" you pick a different server.

This could lead to the system proposing to install a large number up upgrades. If it seems excessive, you can still abort.

---

### Post by priyanshu-gif on 2021-05-18
Really thank you very very much.
now my problem is solved and i able to install texstudio easily in just 2-3 seconds. before this i have spend so many hours in searching the solution of this problem.
you fulfilled my purpose on coming this forum.
thanks a lot! 
Regards
Priyanshu

---

### Post by priyanshu-gif on 2021-05-18
sorry for that. I don't know before this. 
and thank you very much for letting me know this.

---

### Post by Impavidus on 2021-05-18
Great.

I must say that I didn't really expect this problem of a faulty mirror. Usually it's a user doing something not so smart, but there's no way you could have foreseen this.

---

### Post by priyanshu-gif on 2021-05-18
yes, of course but with your help i did it.
BTW how did you know,  that could be the problem?
Thanks a lot again.):P

---

### Post by Impavidus on 2021-05-19
It was mostly this post. I bolded the important bits:
> **priyanshu-gif said:**
> Thank you very much for you help!
i run this and getting this...
```
priyanshu@priyanshu-Inspiron-5593:~$ apt-cache policy texstudio libpoppler-qt5-1 libqt5script5
**texstudio**:
  Installed: (none)
  Candidate: **2.12.16+debian-1.1**
  Version table:
     2.12.16+debian-1.1 500
        500 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal/universe amd64 Packages
**libpoppler-qt5-1**:
  Installed: 0.80.0-0ubuntu4
  Candidate: **0.80.0-0ubuntu4**
  Version table:
 *** 0.80.0-0ubuntu4 500
        500 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal/universe amd64 Packages
        100 /var/lib/dpkg/status
**libqt5script5**:
  Installed: (none)
  Candidate: **5.12.5+dfsg-2**
  Version table:
     5.12.5+dfsg-2 500
        500 [http://repos.del.extreme-ix.org/ubuntu](http://repos.del.extreme-ix.org/ubuntu) focal/universe amd64 Packages
```
On [https://packages.ubuntu.com](https://packages.ubuntu.com) I could find the versions of those packages that are supposed to be in Ubuntu 20.04 by searching for the package name in distribution focal, giving for example [this page]("https://packages.ubuntu.com/focal/texstudio"), telling me that you should have version 2.12.22+debian-1build1. The output above showed 2.12.16+debian-1.1, so that was wrong. On [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) I could find a list of Ubuntu mirrors and the server listed in your output in post 11 is on that list. All entries there are correctly formatted for software sources for Ubuntu 20.04. For example, the line```
deb [http://repos.del.extreme-ix.org/ubuntu/](http://repos.del.extreme-ix.org/ubuntu/) focal main restricted
```tells us you use a deb source from the server on that url, version focal (=20.04) for the main and restricted repositories. But, as you see, the versions of software that repository has available don't match the official versions, so there must be a problem with that mirror.

---

### Post by priyanshu-gif on 2021-05-20
okay, now i got it.
Thank you very much for spending your valuable time in solving  my doubt ,really appreciable.
Regards
Priyanshu

---

