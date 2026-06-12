---
title: "Debconf/dpkg--Cannot install anything or repair broken pacakges"
date: 2015-05-07
forum: MINT
---

### Post by Aspiegeek on 2015-05-07
I am unable to install or repair packages via apt, software center or package  manager. Debconf/dpkg seem to be broken but don't show as such in Syanptic.  
I have tried repairing broken pakages in Syanptic, and also in Recovery Mode,  but attempts to update or install fail with several errors. 
Linux Mint 17.1 Mate x64, fairly recent install.

Running sudo apt-get update:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

I have tried removing the lock file but it seems to reappear any time I run an apt command and I'm back where I started.
Running sudo apt-get install -f:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  evolution-common libevolution libgail-3-0 libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libytnef0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up tzdata (2015d-0ubuntu0.14.04) ...
var/lib/dpkg/info/tzdata.postinst: 9: .: Can't open /usr/share/debconf/confmodule
dpkg: error processing package tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpam-systemd:amd64 (204-5ubuntu20.11) ...
Can't exec "/usr/share/debconf/frontend": No such file or directory at /usr/share/perl5/Debconf/Client/ConfModule.pm line 78.
VERSION 2.0
```

The process freezes at "VERSION 2.0." every time.
**I note that the directory /usr/share/debconf/ does not exist!**
I have disabled all repositories in Software Sources except  mirrors.liquidweb.com/ubuntu  and packages.linuxmint.com
Tried commands autoremove, clean, autoclean, and purge  with similar messages.  Tried reinstalling debconf:

```
$ sudo apt-get install --reinstall debconf
[sudo] password for vince: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)\
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Another set of errors seen a few times:
```
dpkg: error processing package libpam-systemd:amd64 (--configure):
 subprocess installed post-installation script was interrupted
Setting up cpuburn (1.4a-5) ...
/var/lib/dpkg/info/cpuburn.postinst: 5: .: Can't open /usr/share/debconf/confmodule
dpkg: error processing package cpuburn (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of tzdata-java:
 tzdata-java depends on tzdata (= 2015d-0ubuntu0.14.04); however:
  Package tzdata is not configured yet.
dpkg: error processing package tzdata-java (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 libpam-systemd:amd64
 cpuburn
 tzdata-java
```

Ran lsof on the Lock file:
```
$ sudo lsof /var/lib/dpkg/lock
[sudo] password for : 
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF   NODE NAME
dpkg    4065 root    3uW  REG    8,8        0 395032 /var/lib/dpkg/lock

```

I've searched a lot of Linux forums, tried a lot of commands, so far unable to find a solution that works.    Any ideas on how to repair?
Thanks

---

### Post by QIII on 2015-05-07
Hello!

You have a couple of code snippets there that indicate you have more than one package manager interface open.  

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

tells us that.

You can only use one at a time.

Try closing them and opening only one.  That is, if you have the Software Center or synaptic open, close it and use the terminal.

---

### Post by Aspiegeek on 2015-05-07
I checked that earlier and rebooted a few times.  Just rebooted again, ran these commands:
```
$ sudo apt-get update
[sudo] password for *****: 
Ign [http://extra.linuxmint.com](http://extra.linuxmint.com) qiana InRelease
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana InRelease                              
Get:1 [http://extra.linuxmint.com](http://extra.linuxmint.com) qiana Release.gpg [198 B]                     
Get:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana Release.gpg [198 B]                  
Get:3 [http://apt.insynchq.com](http://apt.insynchq.com) qiana InRelease [5,562 B]                        
Ign [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty InRelease                              
Get:4 [http://extra.linuxmint.com](http://extra.linuxmint.com) qiana Release [3,204 B]                       
Get:5 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana Release [24.2 kB]                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates InRelease                      
Get:6 [http://extra.linuxmint.com](http://extra.linuxmint.com) qiana/main amd64 Packages [7,903 B]           
Get:7 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/main amd64 Packages [30.6 kB]        
Get:8 [http://apt.insynchq.com](http://apt.insynchq.com) qiana/non-free amd64 Packages [1,881 B]          
Get:9 [http://extra.linuxmint.com](http://extra.linuxmint.com) qiana/main i386 Packages [7,890 B]            
Get:10 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty Release.gpg [933 B]                 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]          
Get:12 [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg [933 B]                 
Get:13 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates Release.gpg [933 B]         
Get:14 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/upstream amd64 Packages [24.2 kB]   
Get:15 [http://apt.insynchq.com](http://apt.insynchq.com) qiana/contrib amd64 Packages [537 B]            
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [63.5 kB]            
Get:17 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/import amd64 Packages [32.5 kB]     
Get:18 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty Release [58.5 kB]                   
Get:19 [http://archive.canonical.com](http://archive.canonical.com) trusty Release [9,359 B]                   
Get:20 [http://apt.insynchq.com](http://apt.insynchq.com) qiana/non-free i386 Packages [1,884 B]          
Get:21 [http://apt.insynchq.com](http://apt.insynchq.com) qiana/contrib i386 Packages [561 B]             
Get:22 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/main i386 Packages [30.0 kB]        
Get:23 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages [5,567 B]    
Get:24 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates Release [63.5 kB]           
Get:25 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/upstream i386 Packages [24.2 kB]    
Get:26 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages [6,245 B]     
Get:27 [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/import i386 Packages [32.5 kB]      
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [267 kB] 
Get:29 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/main amd64 Packages [1,350 kB]      
Ign [http://extra.linuxmint.com](http://extra.linuxmint.com) qiana/main Translation-en_US                    
Ign [http://extra.linuxmint.com](http://extra.linuxmint.com) qiana/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [8,875 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [101 kB]
Get:32 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/restricted amd64 Packages [13.0 kB] 
Get:33 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/universe amd64 Packages [5,859 kB]  
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [3,681 B]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [256 kB]  
Ign [http://apt.insynchq.com](http://apt.insynchq.com) qiana/contrib Translation-en_US                    
Ign [http://apt.insynchq.com](http://apt.insynchq.com) qiana/contrib Translation-en                       
Ign [http://apt.insynchq.com](http://apt.insynchq.com) qiana/non-free Translation-en_US                   
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/import Translation-en_US               
Ign [http://apt.insynchq.com](http://apt.insynchq.com) qiana/non-free Translation-en                      
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/import Translation-en                  
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/main Translation-en_US                 
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8,846 B]
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/main Translation-en                    
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/upstream Translation-en_US             
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [101 kB]
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) qiana/upstream Translation-en                
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,846 B]
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [136 kB] 
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [1,679 B]
Get:41 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [2,266 B]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [56.8 kB]
Get:43 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/multiverse amd64 Packages [132 kB]  
Get:44 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/main i386 Packages [1,348 kB]       
Get:45 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/restricted i386 Packages [13.4 kB]  
Get:46 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/universe i386 Packages [5,866 kB]   
Get:47 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/multiverse i386 Packages [134 kB]   
Get:48 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/main Translation-en [762 kB]        
Get:49 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/multiverse Translation-en [102 kB]  
Get:50 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/restricted Translation-en [3,457 B] 
Get:51 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/universe Translation-en [4,089 kB]  
Get:52 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/main amd64 Packages [511 kB]
Get:53 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/restricted amd64 Packages [9,238 B]
Get:54 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/universe amd64 Packages [274 kB]
Get:55 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:56 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/main i386 Packages [499 kB] 
Get:57 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/restricted i386 Packages [9,256 B]
Get:58 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/universe i386 Packages [276 kB]
Get:59 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/multiverse i386 Packages [12.1 kB]
Get:60 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/main Translation-en [243 kB]
Get:61 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/multiverse Translation-en [6,148 B]
Get:62 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/restricted Translation-en [2,433 B]
Get:63 [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty-updates/universe Translation-en [143 kB]
Ign [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/main Translation-en_US                 
Ign [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/multiverse Translation-en_US           
Ign [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/restricted Translation-en_US           
Ign [http://mirrors.liquidweb.com](http://mirrors.liquidweb.com) trusty/universe Translation-en_US             
Fetched 23.1 MB in 40s (572 kB/s)                                              
Reading package lists... Done

$ sudo apt-get install --reinstall debconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  evolution-common libevolution libgail-3-0 libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libytnef0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 30 not upgraded.
4 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  evolution-common libevolution libgail-3-0 libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libytnef0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
4 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
```

I have attempted to remove the lock file without effect.

---

### Post by ajgreeny on 2015-05-07
From your repository list in the upgrade output I presume you are using a Mint OS, not Ubuntu.

I do not know what Mint's update arrangements are; does the update-manager start automatically in Mint, and could it already be open, even though you are unaware of the fact that it is running in the background?

---

### Post by QIII on 2015-05-07
Moved to MINT

Good catch ajgreeny.

If Mint behaves differently and updates run automatically or periodically in the background, this is the sort of thing that might happen.

---

### Post by Frogs Hair on 2015-05-07
Try the following. ```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
``` ```
sudo apt-get update
```

---

### Post by Aspiegeek on 2015-05-07
Same as earlier, freezes at "VERSION 2.0"
```
$ sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
[sudo] password for vince: 
                     USER        PID ACCESS COMMAND
/var/lib/dpkg/lock:  root       2937 F.... dpkg
Kill process 2937 ? (y/N) y
Setting up tzdata (2015d-0ubuntu0.14.04) ...
/var/lib/dpkg/info/tzdata.postinst: 9: .: Can't open /usr/share/debconf/confmodule
dpkg: error processing package tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpam-systemd:amd64 (204-5ubuntu20.11) ...
Can't exec "/usr/share/debconf/frontend": No such file or directory at /usr/share/perl5/Debconf/Client/ConfModule.pm line 78.
VERSION 2.0
```

then ^C
```
dpkg: error processing package libpam-systemd:amd64 (--configure):
 subprocess installed post-installation script was interrupted
dpkg: dependency problems prevent configuration of tzdata-java:
 tzdata-java depends on tzdata (= 2015d-0ubuntu0.14.04); however:
  Package tzdata is not configured yet.

dpkg: error processing package tzdata-java (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 libpam-systemd:amd64
 tzdata-java
```

---

### Post by Aspiegeek on 2015-05-07
Also...There are lock files that appear in /var/cache/apt/archives and  var/lib/dpkg, I can "sudo rm" them but they just reappear and I get the  same errors each time I  run any apt, dpkg or install command.  Processes freeze  at "VERSION 2.0" line.

---

### Post by Frogs Hair on 2015-05-08
This was my next suggestion, but  have no more at the moment. If you have unofficial software I would look to that as a possible cause. ```
sudo rm -rf /var/lib/apt/lists/*
``````
sudo apt-get clean 
``````
sudo apt-get update
```

---

### Post by Aspiegeek on 2015-05-08
I tried these commands without success.
> Code:sudo rm -rf /var/lib/apt/lists/* 
 	Code: sudo apt-get clean
 
 	Code: sudo apt-get update
 

The processes seem to be hanging on tzdata and tzdata-java.suao 
```
dependency problems prevent configuration of tzdata-java:  tzdata-java depends on tzdata (= 2015d-0ubuntu0.14.04); however:   Package tzdata is not configured yet
```

I could not start Synaptic due to a running instance of dpkg.  I ran ps aux | grep dpkg and got pid 2706, ran sudo kill -9 2706 to kill dpkg, then Synaptic starts.  I then selected tzdata and tzdata-java for reinstallation.  This fails with message:
```
E: Internal Error, No file name for tzdata:amd64
```
This thread mentions a similar issue, but no solutions are posted: [http://ubuntuforums.org/showthread.php?t=2173793](http://ubuntuforums.org/showthread.php?t=2173793)

Tried this in Terminal with same output:
```
$ sudo apt-get install --reinstall tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 39 not upgraded.
3 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
 $ sudo rm /var/lib/dpkg/lock
 $ sudo rm /var/cache/apt/archives/lock
 $ sudo apt-get install --reinstall tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 39 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for tzdata:amd64

```

Ideas?

---

### Post by Habitual on 2015-05-08
> **Aspiegeek said:**
> Ideas?As a matter of fact, yes. Yes I do have an idea. And only offer this as an extreme measure.
MAKE A BACKUP of /var/lib/dpkg/status
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup
```
and edit 
```
sudo vi /var/lib/dpkg/status
```

and Remove everything in the section|stanza under Package: tzdata ## NOT tzdata-java

and re-install it using
```
sudo apt-get install tzdata
```

Let us know.

Also show us the output of 
```
inxi -Sr
```from a terminal, it this fails to correct the problem for tzdata.

---

### Post by Aspiegeek on 2015-05-09
after editing the  /var/lib/dpkg/status file, and reinstalling tzdata, I got the same hang on VERSION 2.0.

```
$ sudo apt-get install tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tzdata
0 upgraded, 1 newly installed, 0 to remove and 39 not upgraded.
1 not fully installed or removed.
Need to get 170 kB of archives.
After this operation, 1,575 kB of additional disk space will be used.
Get:1 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main tzdata all 2015d-0ubuntu0.14.04 [170 kB]
Fetched 170 kB in 0s (284 kB/s)
Preconfiguring packages ...
/tmp/tzdata.config.EEQJm4: 4: .: Can't open /usr/share/debconf/confmodule
tzdata failed to preconfigure, with exit status 2
Selecting previously unselected package tzdata.
(Reading database ... 192331 files and directories currently installed.)
Preparing to unpack .../tzdata_2015d-0ubuntu0.14.04_all.deb ...
Unpacking tzdata (2015d-0ubuntu0.14.04) ...
Setting up tzdata (2015d-0ubuntu0.14.04) ...
/var/lib/dpkg/info/tzdata.postinst: 9: .: Can't open /usr/share/debconf/confmodule
dpkg: error processing package tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpam-systemd:amd64 (204-5ubuntu20.11) ...
Can't exec "/usr/share/debconf/frontend": No such file or directory at /usr/share/perl5/Debconf/Client/ConfModule.pm line 78.
VERSION 2.0
```

If, instead of killing the hang with ^C, I hit enter repeatedly, I get a series of erros as follows after each enter:

```
Use of uninitialized value $ret[0] in string eq at /usr/share/perl5/Debconf/Client/ConfModule.pm line 134, <STDIN> line 1.
CAPB backup escape

Use of uninitialized value $ret[0] in string eq at /usr/share/perl5/Debconf/Client/ConfModule.pm line 134, <STDIN> line 2.
X_LOADTEMPLATEFILE /var/lib/dpkg/info/libpam-runtime.templates libpam-runtime

Use of uninitialized value $ret[0] in string eq at /usr/share/perl5/Debconf/Client/ConfModule.pm line 134, <STDIN> line 3.
SUBST libpam-runtime/profiles profile_names unix, systemd, gnome-keyring, ecryptfs-utils, consolekit, capability

Use of uninitialized value $ret[0] in string eq at /usr/share/perl5/Debconf/Client/ConfModule.pm line 134, <STDIN> line 4.
SUBST libpam-runtime/profiles profiles Unix authentication, Register user sessions in the systemd control group hierarchy, GNOME Keyring Daemon - Login keyring management, eCryptfs Key/Mount Management, ConsoleKit Session Management, Inheritable Capabilities Management

Use of uninitialized value $ret[0] in string eq at /usr/share/perl5/Debconf/Client/ConfModule.pm line 134, <STDIN> line 5.
SETTITLE libpam-runtime/title

Use of uninitialized value $ret[0] in string eq at /usr/share/perl5/Debconf/Client/ConfModule.pm line 134, <STDIN> line 6.
SET libpam-runtime/profiles unix, systemd, gnome-keyring, ecryptfs-utils, consolekit, capability

Use of uninitialized value $ret[0] in string eq at /usr/share/perl5/Debconf/Client/ConfModule.pm line 134, <STDIN> line 7.
INPUT medium libpam-runtime/profiles
```

Holding down enter will continue the series of mesages for several thousand lines or more...I took it as far as line 2532 with no end in sight.  

```
$ inxi -Sr
System:    Host: vince-OptiPlex-760 Kernel: 3.13.0-24-generic x86_64 (64 bit) Desktop: N/A Distro: Linux Mint 17 Qiana
Repos:     Active apt sources in file: /etc/apt/sources.list.d/insync.list
           deb http://apt.insynchq.com/mint qiana non-free contrib
           Active apt sources in file: /etc/apt/sources.list.d/official-package-repositories.list
           deb http://packages.linuxmint.com qiana main upstream import
           deb http://extra.linuxmint.com qiana main
           deb http://mirrors.liquidweb.com/ubuntu trusty main restricted universe multiverse
           deb http://mirrors.liquidweb.com/ubuntu trusty-updates main restricted universe multiverse
           deb http://security.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse
           deb http://archive.canonical.com/ubuntu/ trusty partner
```

[B]Another obvservation:  
->The directory /usr/share/debconf (referred to in numerous error messages) is empty, it contains no files![/B]

I also found this closed thread with a similar issue and tried the commands listed there without success.
[http://ubuntuforums.org/showthread.php?t=2207684](http://ubuntuforums.org/showthread.php?t=2207684)
```
$ sudo rm /var/lib/apt/lists/lock
rm: cannot remove ‘/var/lib/apt/lists/lock’: No such file or directory
$ sudo rm /var/lib/dpkg/lock
$ sudo rm /var/cache/apt/archives/lock
$ sudo apt-get clean
$ sudo apt-get autoclean --purge
E: Command line option --purge is not understood
$ sudo apt-get autoclean
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
$ sudo dpkg --configure -a
Setting up tzdata (2015d-0ubuntu0.14.04) ...
/var/lib/dpkg/info/tzdata.postinst: 9: .: Can't open /usr/share/debconf/confmodule
dpkg: error processing package tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpam-systemd:amd64 (204-5ubuntu20.11) ...
Can't exec "/usr/share/debconf/frontend": No such file or directory at /usr/share/perl5/Debconf/Client/ConfModule.pm line 78.
VERSION 2.0
```
that now-familiar hang at VERSION 2.0 again...

I continued with removing the lock files again...
```
$ sudo rm /var/lib/dpkg/lock
$ sudo rm /var/lib/apt/lists/lock
rm: cannot remove ‘/var/lib/apt/lists/lock’: No such file or directory
$ sudo rm /var/cache/apt/archives/lock
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gir1.2-gudev-1.0 gir1.2-networkmanager-1.0 gir1.2-wnck-3.0 grub-common
  grub-pc grub-pc-bin grub2-common insync libdrm-intel1 libdrm-intel1:i386
  libdrm-nouveau2 libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386
  libdrm2 libdrm2:i386 libnm-glib-vpn1 libreoffice-base-drivers
  libreoffice-emailmerge libreoffice-java-common
  libreoffice-presentation-minimizer libreoffice-sdbc-hsqldb
  libxml-libxml-perl linux-firmware linux-libc-dev mint-flashplugin-steam
  plymouth-theme-ubuntu-text ppp tcpdump unrar x11-common xorg xserver-xorg
  xserver-xorg-input-all xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-intel xserver-xorg-video-radeon xtrans-dev
39 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 90.1 MB of archives.
After this operation, 6,142 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://packages.linuxmint.com/ qiana/import mint-flashplugin-steam amd64 11.2.202.457 [5,006 kB]
Get:2 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libdrm2 i386 2.4.60-2~ubuntu14.04.1 [24.1 kB]
Get:3 http://apt.insynchq.com/mint/ qiana/non-free insync amd64 1.2.10.35142-trusty [56.1 MB]
Get:4 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libdrm2 amd64 2.4.60-2~ubuntu14.04.1 [23.5 kB]
Get:5 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libdrm-intel1 i386 2.4.60-2~ubuntu14.04.1 [55.2 kB]
Get:6 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libdrm-intel1 amd64 2.4.60-2~ubuntu14.04.1 [55.8 kB]
Get:7 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libdrm-nouveau2 i386 2.4.60-2~ubuntu14.04.1 [14.3 kB]
Get:8 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libdrm-nouveau2 amd64 2.4.60-2~ubuntu14.04.1 [13.7 kB]
Get:9 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libdrm-radeon1 i386 2.4.60-2~ubuntu14.04.1 [24.1 kB]
Get:10 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libdrm-radeon1 amd64 2.4.60-2~ubuntu14.04.1 [23.3 kB]
Get:11 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main plymouth-theme-ubuntu-text amd64 0.8.8-0ubuntu17.1 [7,950 B]
Get:12 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main ppp amd64 2.4.5-5.1ubuntu2.2 [311 kB]
Get:13 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main tcpdump amd64 4.5.1-2ubuntu1.2 [355 kB]
Get:14 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main gir1.2-gudev-1.0 amd64 1:204-5ubuntu20.11 [5,474 B]
Get:15 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main gir1.2-networkmanager-1.0 amd64 0.9.8.8-0ubuntu7.1 [35.4 kB]
Get:16 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main gir1.2-wnck-3.0 amd64 3.4.7-0ubuntu3.1 [8,788 B]
Get:17 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main grub-pc amd64 2.02~beta2-9ubuntu1 [173 kB]
Get:18 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main grub-pc-bin amd64 2.02~beta2-9ubuntu1 [882 kB]
Get:19 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main grub2-common amd64 2.02~beta2-9ubuntu1 [500 kB]
Get:20 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main grub-common amd64 2.02~beta2-9ubuntu1 [1,680 kB]
Get:21 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libnm-glib-vpn1 amd64 0.9.8.8-0ubuntu7.1 [13.1 kB]
Get:22 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libreoffice-base-drivers amd64 1:4.2.8-0ubuntu2 [525 kB]
Get:23 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/universe libreoffice-emailmerge all 1:4.2.8-0ubuntu2 [20.8 kB]
Get:24 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libreoffice-java-common all 1:4.2.8-0ubuntu2 [2,010 kB]
Get:25 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libreoffice-presentation-minimizer all 1:4.2.8-0ubuntu2 [26.5 kB]
Get:26 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libreoffice-sdbc-hsqldb amd64 1:4.2.8-0ubuntu2 [126 kB]
Get:27 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main libxml-libxml-perl amd64 2.0108+dfsg-1ubuntu0.1 [337 kB]
Get:28 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main linux-firmware all 1.127.11 [19.9 MB]
Get:29 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main linux-libc-dev amd64 3.13.0-52.86 [773 kB]
Get:30 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/multiverse unrar amd64 1:5.0.10-1ubuntu0.14.04.1 [117 kB]
Get:31 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main x11-common all 1:7.7+1ubuntu8.1 [49.5 kB]
Get:32 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main xserver-xorg-video-radeon amd64 1:7.3.0-1ubuntu3.1 [121 kB]
Get:33 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main xserver-xorg-video-ati amd64 1:7.3.0-1ubuntu3.1 [6,754 B]
Get:34 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main xserver-xorg-video-intel amd64 2:2.99.910-0ubuntu1.6 [607 kB]
Get:35 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main xserver-xorg-video-all amd64 1:7.7+1ubuntu8.1 [4,546 B]
Get:36 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main xserver-xorg-input-all amd64 1:7.7+1ubuntu8.1 [4,440 B]
Get:37 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main xserver-xorg amd64 1:7.7+1ubuntu8.1 [73.2 kB]
Get:38 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main xorg amd64 1:7.7+1ubuntu8.1 [3,132 B]
Get:39 http://mirrors.liquidweb.com/ubuntu/ trusty-updates/main xtrans-dev all 1.3.5-1~ubuntu14.04.1 [70.3 kB]
Fetched 90.1 MB in 1min 16s (1,181 kB/s)                                       
Extracting templates from packages: 100%
Preconfiguring packages ...
/tmp/grub-pc.config.E1ULQf: 11: .: Can't open /usr/share/debconf/confmodule
grub-pc failed to preconfigure, with exit status 2
/tmp/x11-common.config.Wwwhgr: 10: .: Can't open /usr/share/debconf/confmodule
x11-common failed to preconfigure, with exit status 2
Setting up tzdata (2015d-0ubuntu0.14.04) ...
/var/lib/dpkg/info/tzdata.postinst: 9: .: Can't open /usr/share/debconf/confmodule
dpkg: error processing package tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

removed lock files again,
```
$ sudo dpkg --force-all --configure -a
Setting up tzdata (2015d-0ubuntu0.14.04) ...
/var/lib/dpkg/info/tzdata.postinst: 9: .: Can't open /usr/share/debconf/confmodule
dpkg: error processing package tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpam-systemd:amd64 (204-5ubuntu20.11) ...
Can't exec "/usr/share/debconf/frontend": No such file or directory at /usr/share/perl5/Debconf/Client/ConfModule.pm line 78.
VERSION 2.0
^C
dpkg: error processing package libpam-systemd:amd64 (--configure):
 subprocess installed post-installation script was interrupted
Errors were encountered while processing:
 tzdata
 libpam-systemd:amd64
```

This isn't fun any more.

---

### Post by alex375 on 2015-05-09
sudo dpkg --configure -a

---

### Post by Aspiegeek on 2015-05-09
> sudo dpkg --configure -a 

Tried at least a dozen times.
Hangs at VERSION 2.0:

```
 $ sudo dpkg --configure -a
Setting up tzdata (2015d-0ubuntu0.14.04) ...
/var/lib/dpkg/info/tzdata.postinst: 9: .: Can't open /usr/share/debconf/confmodule
dpkg: error processing package tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpam-systemd:amd64 (204-5ubuntu20.11) ...
Can't exec "/usr/share/debconf/frontend": No such file or directory at /usr/share/perl5/Debconf/Client/ConfModule.pm line 78.
VERSION 2.0
```

---

### Post by Habitual on 2015-05-11
> **Aspiegeek said:**
> 
[B]Another obvservation:  
->The directory /usr/share/debconf (referred to in numerous error messages) is empty, it contains no files![/B]
Maybe reconfigure debconf using:
```
dpkg-reconfigure debconf
``` and then check for content files in **/usr/share/debconf**

After that, I don't know if I'd Frankenstein the debconf infrastructure too much further.

---

### Post by Aspiegeek on 2015-05-11
```
$ sudo dpkg-reconfigure debconf
/var/lib/dpkg/info/debconf.postinst: 42: .: Can't open /usr/share/debconf/confmodule
```

Still no files in that directory...

Any way to manually reinstall the missing files in /usr/share/debconf/confmodule?  Or am I likely stuck with a full reinstall?

---

### Post by Aspiegeek on 2015-05-11
Tried this also:

```
vince@vince-OptiPlex-760 ~ $ sudo dpkg-reconfigure tzdata
/usr/sbin/dpkg-reconfigure: tzdata is broken or not fully installed
```

---

### Post by Habitual on 2015-05-11
How about trying
```
*apt*-*get* install --*reinstall  *debconf
```
and let us know the result.

It may be easier for you to re-install. That depends on partitions/data and the existence of known, good backups.
If there is nothing on this host that causes you to lose sleep, then a re-install should definitely fix it.
But what if that happens again? It would get "old", "quick" to have to repeat this process to exactly the same point.
If you want to know the "why" of it, then I applaud you and your efforts (Props on Documentation btw),
If you just want it to get working/fixed/unbroken, then a re-install would be just the ticket.

Subscribed with interest...

---

### Post by Aspiegeek on 2015-05-11
Back to the same old thing....hang at VERSION 2.0

It seems that debconf, dpkg and tzdata are all broken, and interdependent....stuck in a broken loop...

```
$ sudo apt-get install --reinstall  debconf
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
$ sudo dpkg --configure -a
Setting up tzdata (2015d-0ubuntu0.14.04) ...
/var/lib/dpkg/info/tzdata.postinst: 9: .: Can't open /usr/share/debconf/confmodule
dpkg: error processing package tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpam-systemd:amd64 (204-5ubuntu20.11) ...
Can't exec "/usr/share/debconf/frontend": No such file or directory at /usr/share/perl5/Debconf/Client/ConfModule.pm line 78.
VERSION 2.0
```

There must be some way to fix this without reinstalling.

---

### Post by Habitual on 2015-05-11
I'm fresh out of ideas, sorry.

---

### Post by Habitual on 2015-05-14
OK. 
All I can think of to do is try:
```
sudo dpkg-reconfigure debconf
``` and if that runs without any "FATAL" type reports, then try one of these (or a variant)
```
sudo dpkg-reconfigure tzdata
```
or 
```
sudo apt-get install --reinstall tzdata
```
I do not believe that any one "magic command" is going to fix this for you, so I suggest you take deep breaths and examine closely
the output given in any one single shell command before proceeding to another command.

---

### Post by Aspiegeek on 2015-05-14
Thanks for the suggestions, I believe I've tried all of those before...results:

```
# dpkg-reconfigure debconf
/var/lib/dpkg/info/debconf.postinst: 42: .: Can't open /usr/share/debconf/confmodule
```

....because it does not exist, /usr/share/debconf is empty
```

 # dpkg-reconfigure tzdata
/usr/sbin/dpkg-reconfigure: tzdata is broken or not fully installed
# sudo apt-get install --reinstall tzdata
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

```
# dpkg --configure -a
Setting up tzdata (2015d-0ubuntu0.14.04) ...
/var/lib/dpkg/info/tzdata.postinst: 9: .: Can't open /usr/share/debconf/confmodule
dpkg: error processing package tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpam-systemd:amd64 (204-5ubuntu20.11) ...
Can't exec "/usr/share/debconf/frontend": No such file or directory at /usr/share/perl5/Debconf/Client/ConfModule.pm line 78.
VERSION 2.0
```

...And back to that same old hang again.  
That line 78 in /usr/share/perl5/Debconf/Client/ConfModule.pm reads,
```
exec "/usr/share/debconf/frontend", $0, @ARGV;
```
but, as stated above, "/usr/share/debconf/ is empty.

Content of that file is way beyond my comprehension.

It would seem tzdata, dpkg and debconf are all broken.  Possiblilty of manually reinstalling them?

The irony of this is, the system runs fine and all programs work, except for the inability to install anything.

---

### Post by Habitual on 2015-05-14
I'm fresh out of ideas.

---

