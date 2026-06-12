---
title: "Cannot install Calibre, nor python-pyqt5"
date: 2018-02-09
forum: Installation &amp; Upgrades
---

### Post by adrianstaniec on 2018-02-09
```

**[I] ~ sudo apt install calibre**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 calibre : Depends: python-pyqt5 (>= 5.5.1+dfsg-3ubuntu4) but it is not going to be installed
           Depends: python-pyqt5.qtwebkit but it is not going to be installed
           Depends: python-pyqt5.qtsvg but it is not going to be installed
           Depends: calibre-bin (>= 2.55.0+dfsg-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


**[I] ~ sudo apt install python-pyqt5**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 python-pyqt5 : Depends: qtbase-abi-5-5-1
E: Unable to correct problems, you have held broken packages.


**[I] ~ sudo apt install qtbase-abi-5-5-1**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package qtbase-abi-5-5-1 is a virtual package provided by:
  libqt5core5a 5.5.1+dfsg-16ubuntu7.5 [Not candidate version]
  libqt5core5a 5.5.1+dfsg-16ubuntu7 [Not candidate version]


E: Package 'qtbase-abi-5-5-1' has no installation candidate

**[I] ~ sudo apt install libqt5core5a**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt5core5a is already the newest version (5.6.1+dfsg-3ubuntu1~xenialoverlay1~4+fix1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

:confused:

Can anybody help me understand the issue?

---

### Post by ajgreeny on 2018-02-09
This is one application that will probably install easily and with a much more recent version than that in the repos by going to the calibre website.

Try it at [https://calibre-ebook.com/download_linux](https://calibre-ebook.com/download_linux) using the command shown in the box under **Binary install**
```
sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.py | sudo python -c "import sys; main=lambda:sys.stderr.write('Download failed\n'); exec(sys.stdin.read()); main()"
``` which will install calibre and any dependencies you need with the single command.

---

### Post by TheFu on 2018-02-09
First, do 3 things.
```
sudo apt update
sudo apt dist-upgrade
backup the system

```
Then try ```

sudo apt install calibre
```

Unless you need the latest version, only available from source, I'd stay with the repo version or use a PPA.  The hassles of manually maintaining any package just aren't worth is 99.99999% of the time.  We all get lazy.  I have some installed, important, programs that weren't/aren't maintained via APT, and as crazy as I am about patching, those are months (or worse) behind on updates.  Best to avoid that manual maintenance, whenever possible.

IMHO.

---

### Post by ajgreeny on 2018-02-09
In most situations I agree would with TheFu's feelings about staying with the repos, but for calibre it is worth going out from the repos to get a much newer and better version, 3.17.0. 

I do not know which version of calibre is in your Ubuntu version's repos as you have not told us what version of Ubuntu you are using, but I am fairly certain that it will be much older than that from the calibre site.

I am not on my machine where I have it installed but I think I recall that it tells me if it needs updating when I open it; don't quote me with total certainty about this as my memory may be playing tricks on me.

---

### Post by vasa1 on 2018-02-09
From the code in your first post, there seems something to be the matter with your system. ```
E: Unable to correct problems, you have held broken packages.
```

Have you installed (and removed) ppas in the past? Is this a clean install or an upgrade from one version of Ubuntu to another?

Do ```
sudo apt-get update
```and```
sudo apt-get upgrade
```produce any sort of errors?

---

### Post by TheFu on 2018-02-09
On a 16.04 server, just upgraded last week from 14.04, 
```
$ dpkg -l|grep calib
ii  calibre                                       2.55.0+dfsg-1                                 all          e-book converter and library management
ii  calibre-bin                                   2.55.0+dfsg-1                                 amd64        e-book converter and library management
```

---

### Post by adrianstaniec on 2018-02-09
Wow, thanks everybody for the anwers.

Let me provide some more info.

I have this install for about 10 months, I was originally installed as 16.04,
I did install some things via ppa and also removed some, but I can't recall them specifically.
I thing these command outputs can provide some more info.

```

[B][I] ~ lsb_release -a
[/B]No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

**[I] ~ sudo apt update**
Hit:1 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease
Hit:2 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) xenial InRelease                                                                                             
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                                                                                             
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease                                                                                      
Hit:5 [http://ppa.launchpad.net/apandada1/brightness-controller/ubuntu](http://ppa.launchpad.net/apandada1/brightness-controller/ubuntu) xenial InRelease                                                                 
Ign:6 [http://liveusb.info/multisystem/depot](http://liveusb.info/multisystem/depot) all InRelease                                                                                              
Hit:7 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) xenial-updates InRelease                                                                                     
Ign:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                           
Hit:9 [http://ppa.launchpad.net/ethereum/ethereum-qt/ubuntu](http://ppa.launchpad.net/ethereum/ethereum-qt/ubuntu) xenial InRelease                                                                            
Hit:10 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) xenial-backports InRelease                                                                                  
Hit:11 [http://liveusb.info/multisystem/depot](http://liveusb.info/multisystem/depot) all Release                                                                                               
Hit:12 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                            
Hit:13 [http://ppa.launchpad.net/ethereum/ethereum/ubuntu](http://ppa.launchpad.net/ethereum/ethereum/ubuntu) xenial InRelease                                                                              
Hit:14 [http://ppa.launchpad.net/eugenesan/ppa/ubuntu](http://ppa.launchpad.net/eugenesan/ppa/ubuntu) xenial InRelease                                                                      
Hit:15 [http://storage.googleapis.com/bazel-apt](http://storage.googleapis.com/bazel-apt) stable InRelease                                                                                  
Hit:16 [http://ppa.launchpad.net/fish-shell/release-2/ubuntu](http://ppa.launchpad.net/fish-shell/release-2/ubuntu) xenial InRelease                                                                     
Hit:17 [http://ppa.launchpad.net/flexiondotorg/albert/ubuntu](http://ppa.launchpad.net/flexiondotorg/albert/ubuntu) xenial InRelease                                                                           
Hit:18 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) xenial InRelease                                                                                       
Hit:19 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial InRelease                                                                           
Hit:20 [http://ppa.launchpad.net/kelleyk/emacs/ubuntu](http://ppa.launchpad.net/kelleyk/emacs/ubuntu) xenial InRelease                                                                                  
Hit:21 [http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu](http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu) xenial InRelease                                         
Hit:22 [http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu](http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu) xenial InRelease                                                            
Hit:23 [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) xenial InRelease                                          
Ign:24 [http://www.scootersoftware.com](http://www.scootersoftware.com) bcompare4 InRelease                                 
Hit:25 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                    
Hit:26 [http://www.scootersoftware.com](http://www.scootersoftware.com) bcompare4 Release
Hit:27 [https://download.sublimetext.com](https://download.sublimetext.com) apt/stable/ InRelease
Ign:28 [https://apt.z.cash](https://apt.z.cash) jessie InRelease
Hit:29 [https://apt.z.cash](https://apt.z.cash) jessie Release
Reading package lists... Done 
Building dependency tree       
Reading state information... Done
All packages are up to date.

**[I] ~ sudo apt upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


**[I] ~ sudo apt dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

**[I] ~ sudo apt install calibre**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 calibre : Depends: python-pyqt5 (>= 5.5.1+dfsg-3ubuntu4) but it is not going to be installed
           Depends: python-pyqt5.qtwebkit but it is not going to be installed
           Depends: python-pyqt5.qtsvg but it is not going to be installed
           Depends: calibre-bin (>= 2.55.0+dfsg-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

**[I] ~ dpkg --get-selections | grep hold**
[I] ~ 

```
[FONT=Verdana]
[/FONT]On one hand I am tempted to try the quick fix suggested by  **ajgreeny**.[COLOR=#C61919]
[/COLOR]But on the other hand I agree with the conservatism of **TheFu**.
I did install some things via other repos and ppas in the past,
which might be actually part of the problem now.

So if possible I would like to stick to mainstream stable LTS package versions.

---

### Post by TheFu on 2018-02-09
That is more PPAs on a single machine than I've ever seen.  Those are definitely the issue.  They are conflicting with the official repos.  You have to decide how much effort you want to put into this ...  I would remove all the PPAs and only keep the things from ubuntu.com and canonical.com sources.  

I'd strongly suggest you get into LXD and/or virtualization so you can compartmentalize these different requirements as much as possible in the future.  You might be a good user of flatpak or snap stuff too.

The last thing you might try is to use **aptitude** and have it search for a solution. The only trick is to refuse any "solution" that doesn't look good to you. That will have it keep looking.  Might be worth going through and refusing all of them the first time, to see all the options.

---

### Post by adrianstaniec on 2018-02-09
> **TheFu said:**
> 
That is more PPAs on a single machine than I've ever seen.

Hehe, ok good to know.
I cleaned it a bit. There was a lot of one-off applications.

> **TheFu said:**
> 
  Those are definitely the issue.  They are conflicting with the official repos.  You have to decide how much effort you want to put into this ...  I would remove all the PPAs and only keep the things from ubuntu.com and canonical.com sources.  

Migth be, I am not so sure. There is so far not evidence for it.

> **TheFu said:**
> 
I'd strongly suggest you get into LXD and/or virtualization so you can compartmentalize these different requirements as much as possible in the future.

Maybe in the future I will give it a try, but it looks like a lot of hassle to setup and mental overhead to use.

> **TheFu said:**
> 
You might be a good user of flatpak or snap stuff too.

ASAIK that also requires a PPA ;D

> **TheFu said:**
> 
The last thing you might try is to use **aptitude** and have it search for a solution. The only trick is to refuse any "solution" that doesn't look good to you. That will have it keep looking.  Might be worth going through and refusing all of them the first time, to see all the options.

the onlysolution aptitude sees it not to install the calibre,
even after when I try harder few times:

```

**[I] ~ sudo aptitude install calibre**
The following NEW packages will be installed:
  calibre calibre-bin{ab} libchm1{a} libpodofo0.9.3{a} libtidy-0.99-0{a} python-apsw{a} python-cherrypy3{a} python-cssselect{a} python-cssutils{a} 
  python-dnspython{a} python-feedparser{a} python-markdown{a} python-mechanize{a} python-pyqt5{ab} python-pyqt5.qtsvg{a} python-pyqt5.qtwebkit{a} 
  python-repoze.lru{a} python-routes{a} python-utidylib{a} python-webob{a} python-yaml{a} 
0 packages upgraded, 21 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.8 MB of archives. After unpacking 99.3 MB will be used.
The following packages have unmet dependencies:
 calibre-bin : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                         - libqt5core5a, but 5.6.1+dfsg-3ubuntu1~xenialoverlay1~4+fix1 is installed.                         - libqt5core5a, but 5.6.1+dfsg-3ubuntu1~xenialoverlay1~4+fix1 is installed.
 python-pyqt5 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:
                          - libqt5core5a, but 5.6.1+dfsg-3ubuntu1~xenialoverlay1~4+fix1 is installed.                          - libqt5core5a, but 5.6.1+dfsg-3ubuntu1~xenialoverlay1~4+fix1 is installed.
The following actions will resolve these dependencies:


     Keep the following packages at their current version:
1)     calibre [Not Installed]                            
2)     calibre-bin [Not Installed]                        
3)     python-pyqt5 [Not Installed]                       
4)     python-pyqt5.qtsvg [Not Installed]                 
5)     python-pyqt5.qtwebkit [Not Installed]              


Accept this solution? [Y/n/q/?] n
open: 5028; closed: 7679; defer: 4; conflict: 5                                                                                                        .No solution found within the allotted time.  Try harder? [Y/n] 
Resolving dependencies...
open: 9767; closed: 14671; defer: 4; conflict: 5                                                                                                       .No solution found within the allotted time.  Try harder? [Y/n] 
Resolving dependencies...
open: 14648; closed: 21824; defer: 4; conflict: 5                                                                                                      .No solution found within the allotted time.  Try harder? [Y/n] 
Resolving dependencies...
open: 19642; closed: 29190; defer: 4; conflict: 5                                                                                                      .No solution found within the allotted time.  Try harder? [Y/n] 

```

---

### Post by adrianstaniec on 2018-02-09
OK, it's solved!

Actually the aptitude thing gave me a good hint:

I removed [COLOR=#000000][FONT=&amp]**libqt5core5a** version **5.6.1+dfsg-3ubuntu1~xenialoverlay1~4+fix1 **using** aptitude.**
Along with it I had to remove all packages that depended on it,
(there was a lot of KDE stuff, which I actually don't use).

Next,
[/FONT][/COLOR]I tried to install calibre again using **aptitude**,
and **one of** the suggested resolutions (though **not** the first one)
was to actually install calibre with **libqt5core5a **version** 5.5.1+dfsg-16ubuntu7.5**.
[COLOR=#000000][FONT=&amp][/FONT][/COLOR]:D

[COLOR=#000000][FONT=&amp]Thanks again guys!
I like this forum

[/FONT][/COLOR]

---

### Post by TheFu on 2018-02-09
After you change the repos/PPAs, did you **apt update**?

Snaps work by being self-contained.  All dependencies are included.  Flatpak is the same idea.  

Dependency issues happen in APT for 3 reasons.
* unmaintained systems (update/upgrade)
* manually installed .deb files.  These force dependencies, but don't get updates via APT, unless the .deb file also adds a PPA through the installation process.  Some .deb files do that.
* PPAs that aren't maintained correctly for the specific release.

There are other issues possible, but those are for some sort of failures. 

I use 1 or 2 PPAs per system, max.  
I never install anything via a .deb package anymore.  Every time I have, 6-12 months later, the system would be in "apt hell". I'd have to either do lots of research or just reinstall.  For most of my systems, reinstall takes about 45min and usually whatever was the cause for needing a PPA isn't there any more, so the distro version of the package works fine.

IMHO.

---

### Post by adrianstaniec on 2018-02-10
Ok, clear.
Thanks for this additional explanation, TheFu
I will keep it in mind ;]

---

