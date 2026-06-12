---
title: "mysql problems"
date: 2009-01-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by super.rad on 2009-01-14
I'm getting this message when trying to update
```
benji@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  akonadi-server: Depends: mysql-server-5.0
  mysql-server: Depends: mysql-server-5.0
E: Unmet dependencies. Try using -f.
benji@ubuntu:~$
```
If i try apt-get install -f i get the following
```
benji@ubuntu:~$ sudo apt-get install -f                     
Reading package lists... Done                               
Building dependency tree                                    
Reading state information... Done                           
Correcting dependencies...Done                              
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca
The following NEW packages will be installed
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/26.9MB of archives.
After this operation, 87.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 146065 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu1_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Anyone know how to solve this? Or should I just give it time and it'll work itself out? Thanks

---

### Post by p_quarles on 2009-01-14
> **super.rad said:**
> I'm getting this message when trying to update
```
benji@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  akonadi-server: Depends: mysql-server-5.0
  mysql-server: Depends: mysql-server-5.0
E: Unmet dependencies. Try using -f.
benji@ubuntu:~$
```
If i try apt-get install -f i get the following
```
benji@ubuntu:~$ sudo apt-get install -f                     
Reading package lists... Done                               
Building dependency tree                                    
Reading state information... Done                           
Correcting dependencies...Done                              
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca
The following NEW packages will be installed
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/26.9MB of archives.
After this operation, 87.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 146065 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu1_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Anyone know how to solve this? Or should I just give it time and it'll work itself out? Thanks
That message usually indicates a problem with the package itself, but unfortunately apt-get isn't likely to resolve it without help, and it won't want to fetch the fixed package until the issue broken package is fixed. This is one of those instances where aptitude or synaptic are likely to be of more help.

---

### Post by super.rad on 2009-01-14
well im on kubuntu so I've got adept (which is useless) instead of synaptic. looks like i'm off to read "man aptitude"

---

### Post by p_quarles on 2009-01-14
> **super.rad said:**
> well im on kubuntu so I've got adept (which is useless) instead of synaptic. looks like i'm off to read "man aptitude"
Just try
```
sudo aptitude -f install
```
aptitude's command line works similarly to apt-get, but has a more aggressive dependency/problem resolution system. It also has an ncurses GUI which you can get by running:
```
sudo aptitude
```

---

### Post by super.rad on 2009-01-14
Thanks but I seem to have fixed it, just ran aptitude update then aptitude safe-upgrade and it fixed itself, however after trying to install amarok i'm getting more errors from mysql so I'll leave it a day or so to see if it sorts itself out

---

### Post by Vorian on 2009-01-14
see [http://ubuntuforums.org/showthread.php?t=1038901](http://ubuntuforums.org/showthread.php?t=1038901)

---

### Post by LordVeovis on 2009-01-14
You beat me to it, I was going to link to my post >.<

---

