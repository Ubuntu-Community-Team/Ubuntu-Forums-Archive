---
title: "Error when running Update Manager"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by snyperx on 2007-09-01
I am getting the following message when I attempt to run Update Manager.  Please see attached screen shot.   Thanks!!!

---

### Post by Pumalite on 2007-09-01
Comment(#) line 15 in sources.list
gedit /etc/apt/souces.list
First backup:
cp /etc/apt/sources.list /etc/apt/sources.list.back

---

### Post by snyperx on 2007-09-01
I should have posted this before.  Here are the contents of my sources.list file:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/feisty](http://us.archive.ubuntu.com/ubuntu/feisty) main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/feisty](http://us.archive.ubuntu.com/ubuntu/feisty) main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb [http://us.archive.ubuntu.com/ubuntu/feisty](http://us.archive.ubuntu.com/ubuntu/feisty) universe
deb-src [http://us.archive.ubuntu.com/ubuntu/feisty](http://us.archive.ubuntu.com/ubuntu/feisty) universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/feisty](http://us.archive.ubuntu.com/ubuntu/feisty) multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/feisty](http://us.archive.ubuntu.com/ubuntu/feisty) multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/feisty-backports](http://us.archive.ubuntu.com/ubuntu/feisty-backports) main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/feisty-backports](http://us.archive.ubuntu.com/ubuntu/feisty-backports) main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntufeisty-security](http://security.ubuntu.com/ubuntufeisty-security) main restricted
deb-src [http://security.ubuntu.com/ubuntufeisty-security](http://security.ubuntu.com/ubuntufeisty-security) main restricted
deb [http://security.ubuntu.com/ubuntufeisty-security](http://security.ubuntu.com/ubuntufeisty-security) universe
deb-src [http://security.ubuntu.com/ubuntufeisty-security](http://security.ubuntu.com/ubuntufeisty-security) universe
deb [http://security.ubuntu.com/ubuntufeisty-security](http://security.ubuntu.com/ubuntufeisty-security) multiverse
deb [http://archive.ubuntu.com/ubuntu/feisty-updates](http://archive.ubuntu.com/ubuntu/feisty-updates) restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntufeisty-security](http://security.ubuntu.com/ubuntufeisty-security) multiverse

---

### Post by taurus on 2007-09-01
Close synaptic or whatver update manager you have running right now.  Then, run these two commands from a terminal and see what happens.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by taurus on 2007-09-01
> **Pumalite said:**
> Comment(#) line 15 in sources.list
gedit /etc/apt/souces.list

Probably need to include **gksudo** or else you can't save it (unless you log in as root first).

> First backup:
cp /etc/apt/sources.list /etc/apt/sources.list.back

Need a **sudo** in front for that line as well.

---

### Post by Pumalite on 2007-09-01
Did you change your sources.list recently?. If so; what did you change or in what circumstances?. In one word: What happened?

---

### Post by snyperx on 2007-09-01
When I run update I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@mark-laptop:/etc/apt$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) main Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) main/restricted Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) main Release                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main Release               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) main/restricted Packages                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main/restricted Packages                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) main/restricted Sources                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main/restricted Sources             
Err [http://security.ubuntu.com](http://security.ubuntu.com) main/restricted Packages              
  404 Not Found [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted Release                     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main/restricted Packages            
  404 Not Found [IP: 91.189.89.8 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) main/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/main Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main/restricted Sources
  404 Not Found [IP: 91.189.89.8 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/multiverse Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/universe Packages
  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntufeisty-security/dists/main/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntufeisty-security/dists/main/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/feisty/dists/main/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/feisty/dists/main/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntufeisty-security/dists/main/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntufeisty-security/dists/main/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/feisty/dists/main/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/feisty/dists/main/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by taurus on 2007-09-01
Is your network working?  I didn't have any problem pinging 91.189.88.31 at all.

```

% ping -w 3 91.189.88.31
PING 91.189.88.31 (91.189.88.31) 56(84) bytes of data.
64 bytes from 91.189.88.31: icmp_seq=0 ttl=43 time=123 ms
64 bytes from 91.189.88.31: icmp_seq=1 ttl=43 time=123 ms
64 bytes from 91.189.88.31: icmp_seq=2 ttl=43 time=123 ms

--- 91.189.88.31 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 123.386/123.646/123.921/0.360 ms, pipe 2

```

---

### Post by Pumalite on 2007-09-01
> **taurus said:**
> Probably need to include **gksudo** or else you can't save it (unless you log in as root first).



Need a **sudo** in front for that line as well.

Thanks, taurus.

---

### Post by Pumalite on 2007-09-01
> **snyperx said:**
> When I run update I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@mark-laptop:/etc/apt$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) main Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) main/restricted Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) main Release                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main Release               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) main/restricted Packages                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main/restricted Packages                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) main/restricted Sources                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main/restricted Sources             
Err [http://security.ubuntu.com](http://security.ubuntu.com) main/restricted Packages              
  404 Not Found [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted Release                     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main/restricted Packages            
  404 Not Found [IP: 91.189.89.8 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) main/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/main Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) main/restricted Sources
  404 Not Found [IP: 91.189.89.8 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/multiverse Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) restricted/universe Packages
  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntufeisty-security/dists/main/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntufeisty-security/dists/main/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/feisty/dists/main/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/feisty/dists/main/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntufeisty-security/dists/main/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntufeisty-security/dists/main/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/feisty/dists/main/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/feisty/dists/main/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/feisty-updates/dists/restricted/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

You are now in better hands than mine.

---

### Post by snyperx on 2007-09-01
Yeah, using the same network I have always used.

---

### Post by taurus on 2007-09-01
What's the output of this command from a terminal?

```
ping -w 3 91.189.88.31
```

---

### Post by snyperx on 2007-09-01
PING 91.189.88.31 (91.189.88.31) 56(84) bytes of data.
64 bytes from 91.189.88.31: icmp_seq=1 ttl=49 time=108 ms
64 bytes from 91.189.88.31: icmp_seq=2 ttl=49 time=108 ms
64 bytes from 91.189.88.31: icmp_seq=2 ttl=49 time=112 ms (DUP!)
64 bytes from 91.189.88.31: icmp_seq=3 ttl=49 time=109 ms
64 bytes from 91.189.88.31: icmp_seq=3 ttl=49 time=113 ms (DUP!)

---

### Post by snyperx on 2007-09-04
Can someone just post a copy of there sources.list file?  Looks like no one can help me otherwise.  Thanks.

---

### Post by taurus on 2007-09-04
```

# 
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

# Commercial...
deb http://archive.canonical.com/ubuntu feisty-commercial main

```

---

