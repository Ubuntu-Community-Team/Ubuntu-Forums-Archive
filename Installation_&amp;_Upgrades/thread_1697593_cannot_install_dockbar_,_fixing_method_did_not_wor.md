---
title: "cannot install dockbar , fixing method did not work."
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by maizuddin35 on 2011-03-01
Hello guys, I want to install dockbar x and this output come out 

```
adibizuddin@maizuddin35:~$ sudo apt-get install dockbarx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dockbarx is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 dockmanager-daemon : Depends: dockmanager (= 0.1.0~bzr80-0ubuntu1~10.10~dockers1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```and when I apt-get -f install :
```
adibizuddin@maizuddin35:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  dockmanager
The following NEW packages will be installed:
  dockmanager
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
6 not fully installed or removed.
Need to get 0B/94.9kB of archives.
After this operation, 430kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  dockmanager
Install these packages without verification [y/N]? y
(Reading database ... 229708 files and directories currently installed.)
Unpacking dockmanager (from .../dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb (--unpack):
 trying to overwrite '/usr/share/dockmanager/data/skype_away.svg', which is also in package faenza-icon-theme 0.8
Errors were encountered while processing:
 /var/cache/apt/archives/dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
adibizuddin@maizuddin35:~$ 

```I follow this method of fixing this, from here [http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html](http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html)
and here is the output from :

fixing code :```
sudo dpkg -i --force-overwrite  /var/cache/apt/archives/smplayer_0.6.9+svn3595-1ppa1~maverick1_i386.deb
```Output  : 
```
adibizuddin@maizuddin35:~$ sudo dpkg -i --force-all  var/apt/cache/archives/dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb
dpkg: error processing var/apt/cache/archives/dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 var/apt/cache/archives/dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb

```what should I do ?

---

### Post by maizuddin35 on 2011-03-01
it seems there is nothing happen. and when I want to remove --purge the package and try to install it back, it does not work, now it need to be fix first then I can do my update and upgrade on my package

anyone?

---

### Post by maizuddin35 on 2011-03-01
I think I fixed it now :)

Here are my first output when I want to install it with -f install :

```
adibizuddin@maizuddin35:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  dockmanager
The following NEW packages will be installed:
  dockmanager
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
5 not fully installed or removed.
Need to get 0B/94.9kB of archives.
After this operation, 430kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  dockmanager
Install these packages without verification [y/N]? y
(Reading database ... 229708 files and directories currently installed.)
Unpacking dockmanager (from .../dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb (--unpack):
 trying to overwrite '/usr/share/dockmanager/data/skype_away.svg', which is also in package faenza-icon-theme 0.8
Errors were encountered while processing:
 /var/cache/apt/archives/dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I miss look that it has error while processing the **DOCKMANAGER **, and then I write the same code fix with the different package that is the dockmanager :

```
sudo dpkg -i --force-all /var/cache/apt/archives/dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb 

```

The output is this :
```
adibizuddin@maizuddin35:~$ sudo dpkg -i --force-all /var/cache/apt/archives/dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb 
(Reading database ... 229708 files and directories currently installed.)
Unpacking dockmanager (from .../dockmanager_0.1.0~bzr80-0ubuntu1~10.10~dockers1_i386.deb) ...
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/dockmanager/data/skype_away.svg', which is also in package faenza-icon-theme 0.8
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/dockmanager/data/skype_na.svg', which is also in package faenza-icon-theme 0.8
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/dockmanager/data/skype_skypeme.svg', which is also in package faenza-icon-theme 0.8
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/dockmanager/data/skype_dnd.svg', which is also in package faenza-icon-theme 0.8
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/dockmanager/data/skype_online.svg', which is also in package faenza-icon-theme 0.8
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/dockmanager/data/skype_offline.svg', which is also in package faenza-icon-theme 0.8
dpkg: warning: overriding problem because --force enabled:
 trying to overwrite '/usr/share/dockmanager/data/skype_invisible.svg', which is also in package faenza-icon-theme 0.8
dpkg: also configuring `python-dockmanager' (required by `dockmanager')
Setting up python-dockmanager (0.1.0~bzr80-0ubuntu1~10.10~dockers1) ...
Setting up dockmanager (0.1.0~bzr80-0ubuntu1~10.10~dockers1) ...
Processing triggers for python-support ...

```

I try again with apt-get -f install and it run back to normal. :)

---

