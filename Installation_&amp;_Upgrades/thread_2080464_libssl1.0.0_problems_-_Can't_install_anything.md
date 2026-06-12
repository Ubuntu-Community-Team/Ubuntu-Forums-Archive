---
title: "libssl1.0.0 problems - Can't install anything"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by Spaziba on 2012-11-04
Hi!
I've searched the forum for solutions and there are some people having the same problem as i have. However, i tried all of those and i can't really it straight. 

 Ubuntu 12.04.1 LTS

When I try to install something i can't do it due to some dependencies of packages:
```
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl1.0.0 : Breaks: libssl1.0.0:i386 (!= 1.0.1-4ubuntu5.5) but 1.0.0e-2ubuntu4.5 is to be installed
 libssl1.0.0:i386 : Breaks: libssl1.0.0 (!= 1.0.0e-2ubuntu4.5) but 1.0.1-4ubuntu5.5 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Running: apt-get -f install
gives: 
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl1.0.0:i386
The following packages will be upgraded:
  libssl1.0.0:i386
1 upgraded, 0 newly installed, 0 to remove and 64 not upgraded.
6 not fully installed or removed.
Need to get 0 B/1,003 kB of archives.
After this operation, 23.6 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Internal Error, No file name for libssl1.0.0

```

I've seen that people prompting: apt-cache policy libssl-dev
which gives me: 
```

libssl-dev:
  Installed: (none)
  Candidate: 1.0.1-4ubuntu5.5
  Version table:
     1.0.1-4ubuntu5.5 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
     1.0.1-4ubuntu5.3 0
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
     1.0.1-4ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages

```

I am a total beginner of servers and Ubuntu. I think i messed it all up when i installed bacula and my internet connection died. To solve that i removed something (not that smart :( ) And now i am here. I also runned an update before that. Can someone help me?

---

### Post by Spaziba on 2012-11-04
Hi,

I am definetly a beginner. I realised that i didn't reboot after the the network connection failure. Then it was just to install the correct libssl, run update/clean.

So it's solved

---

