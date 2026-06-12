---
title: "Error while trying to reinstall  banshee"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by GerardGG on 2010-12-17
I had problems running banshee on ubuntu 10.04 LTS so I removed it using the ubuntu software center. When trying to re- install from the banshee website i get this message: 

Can not install "banshee" (E: Unable to correct problems, you have held broken packages.)

I tried to remove anything associated with banshee on the synaptic package manager but no packages appeared to be installed or broken.

When running $ sudo apt-get install -f

I get this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry [http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu/](http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu/) jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_banshee-team_banshee-unstable_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
gerardo@lapger:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory

Any idea on how to find and remove the so called broken packages?
Thanks in advance.

---

### Post by sikander3786 on 2010-12-18
Welcome to the forums :-)

Post the output of these commands.

```
cat /etc/apt/sources.list
```

```
sudo apt-get update
```

And you need to run apt-get update with sudo infront to gain root privileges ;-)

While posting, click the # icon in post menu and paste your text in between the generated code tags individually for both the outputs.

Thanks.

---

### Post by GerardGG on 2010-12-18
```
gerardo@lapger:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe
# deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu karmic main # disabled on upgrade to karmic
# deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu karmic main # disabled on upgrade to karmic

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://mx.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://mx.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse


# deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu karmic main deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main # disabled on upgrade to karmic
# deb http://blognux.free.fr/ubuntu hardy main # disabled on upgrade to karmic
# deb-src http://blognux.free.fr/ubuntu hardy main # disabled on upgrade to karmic
# deb http://apt.wicd.net gutsy extras # disabled on upgrade to karmic
# deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu lucid main # disabled on upgrade to lucid
deb http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu jaunty main deb-src http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu jaunty main
deb http://archive.ubuntu.com/ubuntu lucid-backports restricted main multiverse universe

``````
gerardo@lapger:~$ sudo apt-get update
[sudo] password for gerardo: 
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu/ jaunty/main Translation-en_GB
Ign http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu/ jaunty/deb-src Translation-en_GB
Hit http://archive.ubuntu.com lucid Release.gpg
Hit http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB
Ign http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu/ jaunty/http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu Translation-en_GB
Ign http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu/ jaunty/jaunty Translation-en_GB
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_GB
Hit http://ppa.launchpad.net jaunty Release    
Hit http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB
Hit http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB
Hit http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB
Get: 1 http://archive.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
Hit http://archive.ubuntu.com lucid-security Release.gpg             
Hit http://ppa.launchpad.net lucid Release                           
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Hit http://archive.ubuntu.com lucid-backports Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_GB
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_GB
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://archive.ubuntu.com lucid Release    
Get: 2 http://archive.ubuntu.com lucid-updates Release [44.7kB]      
Hit http://ppa.launchpad.net lucid/main Packages                           
Hit http://archive.ubuntu.com lucid-security Release   
Hit http://archive.ubuntu.com lucid-backports Release
Hit http://archive.ubuntu.com lucid/main Packages
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid/multiverse Sources
Get: 3 http://archive.ubuntu.com lucid-updates/main Packages [370kB]
Get: 4 http://archive.ubuntu.com lucid-updates/restricted Packages [3,240B]
Get: 5 http://archive.ubuntu.com lucid-updates/main Sources [141kB]
Get: 6 http://archive.ubuntu.com lucid-updates/restricted Sources [1,443B]
Get: 7 http://archive.ubuntu.com lucid-updates/universe Packages [159kB]
Get: 8 http://archive.ubuntu.com lucid-updates/universe Sources [61.3kB]
Get: 9 http://archive.ubuntu.com lucid-updates/multiverse Packages [7,366B]    
Get: 10 http://archive.ubuntu.com lucid-updates/multiverse Sources [3,677B]    
Hit http://archive.ubuntu.com lucid-security/main Packages                     
Hit http://archive.ubuntu.com lucid-security/restricted Packages               
Hit http://archive.ubuntu.com lucid-security/main Sources                      
Hit http://archive.ubuntu.com lucid-security/restricted Sources                
Hit http://archive.ubuntu.com lucid-security/universe Packages                 
Hit http://archive.ubuntu.com lucid-security/universe Sources                  
Hit http://archive.ubuntu.com lucid-security/multiverse Packages               
Hit http://archive.ubuntu.com lucid-security/multiverse Sources                
Hit http://archive.ubuntu.com lucid-backports/restricted Packages              
Hit http://archive.ubuntu.com lucid-backports/main Packages                    
Hit http://archive.ubuntu.com lucid-backports/multiverse Packages              
Hit http://archive.ubuntu.com lucid-backports/universe Packages                
Fetched 792kB in 6s (122kB/s)                                                  
W: Failed to fetch http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu/dists/jaunty/Release  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
gerardo@lapger:~$ 

```

Thank you.

---

### Post by sikander3786 on 2010-12-18
Edit your sources.list,

```
gksudo gedit /etc/apt/sources.list
```

And comment this line (2nd last in that file) in the beginning with a #.

```
deb http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu jaunty main deb-src http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu jaunty main

```

So it looks like,

```
#deb http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu jaunty main deb-src http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu jaunty main

```

Save and close and again try apt-get update and apt-get install -f.

---

### Post by GerardGG on 2010-12-24
Worked like a charm. Thank you very much. Im again running banshee just in time to adjust the Christmas play list.

---

