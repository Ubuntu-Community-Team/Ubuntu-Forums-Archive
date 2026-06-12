---
title: "Ubuntu 20.04.2 openssh installation issues"
date: 2021-06-28
forum: Installation &amp; Upgrades
---

### Post by itsshowtime on 2021-06-28
Hi guys,


I am experiencing weird issues with the installation of openssh on an out of the box Ubuntu 20.04.2 LTS. I will give you the outputs I am getting;


Version Information:
```

madelaet@Pod1-SFTP:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal

```


update check:
```

adelaet@Pod1-SFTP:~$ sudo apt update
Hit:1 http://be.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://be.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:3 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]    
Get:4 http://be.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB] 
Reading package lists... Done      
E: Release file for http://be.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease is not valid yet (invalid for another 6h 38min 3s). Updates for this repository will not be applied.
E: Release file for http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease is not valid yet (invalid for another 7h 7min 42s). Updates for this repository will not be applied.
E: Release file for http://be.archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease is not valid yet (invalid for another 6h 38min 38s). Updates for this repository will not be applied.

```


ssh:
```

madelaet@Pod1-SFTP:~$ sudo apt install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ssh : Depends: openssh-server (>= 1:8.2p1-4)
E: Unable to correct problems, you have held broken packages.

```


Check for broken packages (none seem to be broken):
```

madelaet@Pod1-SFTP:~$ sudo apt-get --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


openssh-server:
```

madelaet@Pod1-SFTP:~$ sudo apt install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:8.2p1-4)
                  Depends: openssh-sftp-server
                  Recommends: ssh-import-id but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```


ssh-import-id (installed this few hours ago):
```

madelaet@Pod1-SFTP:~$ sudo apt install ssh-import-id
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ssh-import-id is already the newest version (5.10-0ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


openssh-sftp-server (where we start to loop):
```

madelaet@Pod1-SFTP:~$ sudo apt install openssh-sftp-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 openssh-sftp-server : Depends: openssh-client (= 1:8.2p1-4)
                       Recommends: openssh-server or
                                   ssh-server
E: Unable to correct problems, you have held broken packages.

```


As you can see I am very much stuck in this dependency loop, it's really weird behavior, especially considering this is a fresh install of an Ubuntu LTS release. Any guidance would be appreciated.

---

### Post by deadflowr on 2021-06-28
Your update check failed.
Everything after that was bound to fail as well.

The issue seems to be your clock is set to the wrong time.
See:[https://itsfoss.com/fix-repository-not-valid-yet-error-ubuntu/]("https://itsfoss.com/fix-repository-not-valid-yet-error-ubuntu/")

---

### Post by itsshowtime on 2021-07-14
Hi Deadflowr,

I forgot to reply. Seems like you spotted the issue, thanks a lot!

---

### Post by deadflowr on 2021-07-14
It's okay.
The forums recently under went some maintenance,
which has/had left some lingering posting issues.
Most are resolved now.
So it's probably a good thing you replied a little later.

That said,
if your issues have been solved please mark this thread as solved:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

