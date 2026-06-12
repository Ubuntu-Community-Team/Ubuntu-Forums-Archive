---
title: "upgrade problem: broken packages"
date: 2013-03-04
forum: Installation &amp; Upgrades
---

### Post by de_pol on 2013-03-04
Hi, I have a broken package on my system, and I don't seem to be able to resolve this issue... :confused:

my version:
```
uname -a
Linux lpt-remy 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
sudo apt-get update
Ign http://security.ubuntu.com quantal-security InRelease
Ign http://ppa.launchpad.net quantal InRelease                      
Ign http://be.archive.ubuntu.com quantal InRelease                   
Ign http://dl.google.com stable InRelease                            
Hit http://security.ubuntu.com quantal-security Release.gpg          
Hit http://ppa.launchpad.net quantal Release.gpg                     
Ign http://be.archive.ubuntu.com quantal-updates InRelease           
Hit http://security.ubuntu.com quantal-security Release                        
Ign http://be.archive.ubuntu.com quantal-backports InRelease                   
Hit http://ppa.launchpad.net quantal Release                         
Hit http://be.archive.ubuntu.com quantal Release.gpg                           
Hit http://security.ubuntu.com quantal-security/main Sources                   
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://be.archive.ubuntu.com quantal-updates Release.gpg         
Hit http://security.ubuntu.com quantal-security/restricted Sources             
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://be.archive.ubuntu.com quantal-backports Release.gpg                 
Hit http://security.ubuntu.com quantal-security/universe Sources               
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://be.archive.ubuntu.com quantal Release                               
Hit http://security.ubuntu.com quantal-security/multiverse Sources             
Hit http://be.archive.ubuntu.com quantal-updates Release                       
Hit http://security.ubuntu.com quantal-security/main amd64 Packages            
Hit http://be.archive.ubuntu.com quantal-backports Release                     
Hit http://security.ubuntu.com quantal-security/restricted amd64 Packages      
Hit http://be.archive.ubuntu.com quantal/main Sources                          
Hit http://security.ubuntu.com quantal-security/universe amd64 Packages
Hit http://be.archive.ubuntu.com quantal/restricted Sources                    
Hit http://security.ubuntu.com quantal-security/multiverse amd64 Packages      
Hit http://be.archive.ubuntu.com quantal/universe Sources                      
Hit http://security.ubuntu.com quantal-security/main i386 Packages             
Hit http://dl.google.com stable Release.gpg                          
Hit http://be.archive.ubuntu.com quantal/multiverse Sources          
Hit http://security.ubuntu.com quantal-security/restricted i386 Packages
Hit http://be.archive.ubuntu.com quantal/main amd64 Packages         
Hit http://security.ubuntu.com quantal-security/universe i386 Packages         
Hit http://be.archive.ubuntu.com quantal/restricted amd64 Packages             
Hit http://security.ubuntu.com quantal-security/multiverse i386 Packages       
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Hit http://be.archive.ubuntu.com quantal/universe amd64 Packages               
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Hit http://be.archive.ubuntu.com quantal/multiverse amd64 Packages             
Hit http://security.ubuntu.com quantal-security/main Translation-en  
Hit http://be.archive.ubuntu.com quantal/main i386 Packages
Hit http://be.archive.ubuntu.com quantal/restricted i386 Packages
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en
Hit http://be.archive.ubuntu.com quantal/universe i386 Packages      
Hit http://be.archive.ubuntu.com quantal/multiverse i386 Packages    
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Hit http://be.archive.ubuntu.com quantal/main Translation-en         
Hit http://security.ubuntu.com quantal-security/universe Translation-en
Hit http://be.archive.ubuntu.com quantal/multiverse Translation-en   
Hit http://be.archive.ubuntu.com quantal/restricted Translation-en
Hit http://be.archive.ubuntu.com quantal/universe Translation-en
Hit http://be.archive.ubuntu.com quantal-updates/main Sources        
Hit http://dl.google.com stable Release                              
Hit http://be.archive.ubuntu.com quantal-updates/restricted Sources   
Hit http://dl.google.com stable/main amd64 Packages
Hit http://be.archive.ubuntu.com quantal-updates/universe Sources
Hit http://be.archive.ubuntu.com quantal-updates/multiverse Sources
Hit http://dl.google.com stable/main i386 Packages
Hit http://be.archive.ubuntu.com quantal-updates/main amd64 Packages
Hit http://be.archive.ubuntu.com quantal-updates/restricted amd64 Packages
Hit http://be.archive.ubuntu.com quantal-updates/universe amd64 Packages
Ign http://security.ubuntu.com quantal-security/main Translation-en_US
Hit http://be.archive.ubuntu.com quantal-updates/multiverse amd64 Packages
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Hit http://be.archive.ubuntu.com quantal-updates/main i386 Packages  
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Hit http://be.archive.ubuntu.com quantal-updates/restricted i386 Packages
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Hit http://be.archive.ubuntu.com quantal-updates/universe i386 Packages
Hit http://be.archive.ubuntu.com quantal-updates/multiverse i386 Packages
Hit http://be.archive.ubuntu.com quantal-updates/main Translation-en
Hit http://be.archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://be.archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://be.archive.ubuntu.com quantal-updates/universe Translation-en
Hit http://be.archive.ubuntu.com quantal-backports/main Sources
Hit http://be.archive.ubuntu.com quantal-backports/restricted Sources
Hit http://be.archive.ubuntu.com quantal-backports/universe Sources
Hit http://be.archive.ubuntu.com quantal-backports/multiverse Sources
Hit http://be.archive.ubuntu.com quantal-backports/main amd64 Packages
Hit http://be.archive.ubuntu.com quantal-backports/restricted amd64 Packages
Hit http://be.archive.ubuntu.com quantal-backports/universe amd64 Packages
Hit http://be.archive.ubuntu.com quantal-backports/multiverse amd64 Packages
Hit http://be.archive.ubuntu.com quantal-backports/main i386 Packages
Hit http://be.archive.ubuntu.com quantal-backports/restricted i386 Packages
Hit http://be.archive.ubuntu.com quantal-backports/universe i386 Packages
Hit http://be.archive.ubuntu.com quantal-backports/multiverse i386 Packages
Hit http://be.archive.ubuntu.com quantal-backports/main Translation-en
Hit http://be.archive.ubuntu.com quantal-backports/multiverse Translation-en
Hit http://be.archive.ubuntu.com quantal-backports/restricted Translation-en
Hit http://be.archive.ubuntu.com quantal-backports/universe Translation-en
Ign http://be.archive.ubuntu.com quantal/main Translation-en_US
Ign http://be.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://be.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://be.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://be.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://be.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://be.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://be.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://be.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://be.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://be.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://be.archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Reading package lists... Done
```

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libgl1-mesa-dri : Depends: libdrm-nouveau2 (>= 2.4.34) but it is not installed
E: Unmet dependencies. Try using -f.
```

```
sudo apt-get -fy install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libdrm-intel1:i386 libdrm-nouveau1a:i386 libdrm-radeon1:i386
  libpciaccess0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdrm-nouveau2
The following NEW packages will be installed:
  libdrm-nouveau2
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
2 not fully installed or removed.
Need to get 0 B/15.1 kB of archives.
After this operation, 88.1 kB of additional disk space will be used.
(Reading database ... 477461 files and directories currently installed.)
Unpacking libdrm-nouveau2:amd64 (from .../libdrm-nouveau2_2.4.39-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libdrm_nouveau.so.2.0.0', which is also in package libdrm-nouveau1a:amd64 2.4.40~precise~ppa1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
sudo apt-get -fy remove libdrm-nouveau1a 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgl1-mesa-dri : Depends: libdrm-nouveau2 (>= 2.4.34) but it is not going to be installed
 plymouth : Depends: libdrm-nouveau1a (>= 2.4.23) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

sudo apt-get -fy install libgl1-mesa-dri
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgl1-mesa-dri is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgl1-mesa-dri : Depends: libdrm-nouveau2 (>= 2.4.34) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

```

sudo apt-get -fy install libdrm-nouveau2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdrm-intel1:i386 libdrm-nouveau1a:i386 libdrm-radeon1:i386
  libpciaccess0:i386
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libdrm-nouveau2
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
2 not fully installed or removed.
Need to get 0 B/15.1 kB of archives.
After this operation, 88.1 kB of additional disk space will be used.
(Reading database ... 477461 files and directories currently installed.)
Unpacking libdrm-nouveau2:amd64 (from .../libdrm-nouveau2_2.4.39-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libdrm_nouveau.so.2.0.0', which is also in package libdrm-nouveau1a:amd64 2.4.40~precise~ppa1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I hope you guys can help me...

kr,
de_pol

---

### Post by cortman on 2013-03-04
Run

```
sudo rm -r /var/cache/apt/archives/*
```

This will remove downloaded debs, in case one was corrupted.

Next run

```
sudo apt-get install -f
```

---

### Post by de_pol on 2013-03-04
thanks for the reply, but this didn't solve the problem (I also tried this already)

```
sudo rm -r /var/cache/apt/archives/*
[sudo] password for remy: 
remy@lpt-remy:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libdrm-intel1:i386 libdrm-nouveau1a:i386 libdrm-radeon1:i386
  libpciaccess0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdrm-nouveau2
The following NEW packages will be installed:
  libdrm-nouveau2
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
2 not fully installed or removed.
Need to get 15.1 kB of archives.
After this operation, 88.1 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://be.archive.ubuntu.com/ubuntu/ quantal/main libdrm-nouveau2 amd64 2.4.39-0ubuntu1 [15.1 kB]
Fetched 15.1 kB in 0s (90.8 kB/s)          
(Reading database ... 477461 files and directories currently installed.)
Unpacking libdrm-nouveau2:amd64 (from .../libdrm-nouveau2_2.4.39-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libdrm_nouveau.so.2.0.0', which is also in package libdrm-nouveau1a:amd64 2.4.40~precise~ppa1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by cortman on 2013-03-04
Looks like this is a known bug. [https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1093517](https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/1093517)
This has worked for some people- force reinstalling the package-

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --force-remove-reinstreq -r libdrm-nouveau2
```

Give it a try.[/FONT][/COLOR]

---

### Post by de_pol on 2013-03-04
Hi, thanks for your reply. Still no luck though...

```

sudo dpkg --force-remove-reinstreq -r libdrm-nouveau1a 
[sudo] password for remy: 
dpkg: dependency problems prevent removal of libdrm-nouveau1a:amd64:
 plymouth depends on libdrm-nouveau1a (>= 2.4.23).

dpkg: error processing libdrm-nouveau1a:amd64 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libdrm-nouveau1a:amd64
remy@lpt-remy:~$ sudo dpkg --force-remove-reinstreq -r libdrm-nouveau2
dpkg: warning: ignoring request to remove libdrm-nouveau2:amd64 which isn't installed
```

---

### Post by cortman on 2013-03-04
Did you get these files from a ppa?

---

### Post by fofafik on 2013-03-08
I have similar problem and the reason is like there:
[http://www.absolutelytech.com/2010/06/30/solved-error-dpkg-error-processing-filename-unpack-trying-to-overwrite/](http://www.absolutelytech.com/2010/06/30/solved-error-dpkg-error-processing-filename-unpack-trying-to-overwrite/)

sudo dpkg -i --force-overwrite /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_amd64.deb
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_i386.deb
sudo apt-get -f install

---

### Post by mariomoralesrivera on 2014-01-17
Thanks, it worked for me.

---

### Post by Zhivargo on 2014-01-20
change thread to [Solved]

---

### Post by Iowan on 2014-01-20
> **Zhivargo said:**
> change thread to [Solved]Only **de_pol** or staff can do that. ;)

---

