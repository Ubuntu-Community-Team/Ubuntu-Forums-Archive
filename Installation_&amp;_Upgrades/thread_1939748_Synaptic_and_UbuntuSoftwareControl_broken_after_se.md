---
title: "Synaptic and UbuntuSoftwareControl broken after security upgrade."
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by Helen McCall on 2012-03-12
This morning my upgrade manager posted some upgrades for Chromium (3 packages) and for tzdata (2 packages). Since upgrading these with the upgrade manager, I've found that both synaptic and Ubuntu Software Control are broken. I have tried re-booting but problem persisted.

USC is running and lists packages in most sections, but when the section "system" is selected it just hangs.

synaptic which is my primary choice for installing packages, crashes when I try to launch it. Launching from a terminal to give the error message, comes up with this response:
[INDENT]helen@helen-GA-A75-D3H:~$ synaptic
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Aborted
[/INDENT]The syslog entry for this termination is as follows:
[INDENT]Mar 12 12:52:12 helen-GA-A75-D3H AptDaemon: INFO: Quitting due to inactivity
Mar 12 12:52:12 helen-GA-A75-D3H AptDaemon: INFO: Quitting was requested

[/INDENT]Can anyone help with any suggestions as to what has gone wrong and how I might fix it?

Best wishes, Helen

---

### Post by Frogs Hair on 2012-03-12
Hello and Welcome

Post your Ubuntu version and have a look at the link . [https://answers.launchpad.net/ubuntu/+source/aptdaemon/+question/129894](https://answers.launchpad.net/ubuntu/+source/aptdaemon/+question/129894)

---

### Post by Helen McCall on 2012-03-12
Hi Frogs Hair

My Ubuntu version is 11:10

Yes it looks like something similar.

Here is my debug output:

helen@helen-GA-A75-D3H:~$ sudo aptd --debug
[sudo] password for helen: 
15:31:36 AptDaemon [INFO]: Initializing daemon
15:31:36 AptDaemon [DEBUG]: Setting up worker thread
15:31:36 AptDaemon [DEBUG]: Daemon was initialized
15:31:36 AptDaemon [DEBUG]: Using inactivity check
15:31:36 AptDaemon [DEBUG]: Waiting for calls
15:31:36 AptDaemon [DEBUG]: GetAll() was called: org.debian.apt
15:31:36 AptDaemon [INFO]: UpgradeSystem() was called with safe mode: 1
15:31:36 AptDaemon [DEBUG]: GetAll() was called: org.debian.apt.transaction
15:31:36 AptDaemon.Trans [INFO]: Simulate was called
15:31:36 AptDaemon.Worker [INFO]: Simulating trans: /org/debian/apt/transaction/170c36f58b1648978a28f139f06506f3
15:31:36 AptDaemon.Trans [DEBUG]: Emitting PropertyChanged: Status, status-resolving-dep
15:31:36 AptDaemon.Trans [DEBUG]: Emitting PropertyChanged: Status, status-loading-cache
15:31:37 AptDaemon.Worker [INFO]: Upgrade system with safe mode: 1
15:31:37 AptDaemon.Trans [DEBUG]: Emitting PropertyChanged: Status, status-resolving-dep
15:31:38 AptDaemon.Worker [DEBUG]: There isn't any registered modify_cache_before plugin
15:31:38 AptDaemon.Worker [DEBUG]: There isn't any registered modify_cache_after plugin
15:31:39 AptDaemon.Trans [DEBUG]: Emitting PropertyChanged: Dependencies, dbus.Struct((dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))), signature=dbus.Signature('as'))
15:31:39 AptDaemon.Trans [DEBUG]: Emitting PropertyChanged: Download, 0
15:31:39 AptDaemon.Trans [DEBUG]: Emitting PropertyChanged: Space, 0
15:31:39 AptDaemon.Trans [DEBUG]: Emitting PropertyChanged: Unauthenticated, dbus.Array([], signature=dbus.Signature('s'))
15:31:39 AptDaemon.Trans [DEBUG]: Emitting PropertyChanged: Status, status-setting-up
15:32:36 AptDaemon [DEBUG]: Checking for inactivity
15:33:36 AptDaemon [DEBUG]: Checking for inactivity
15:34:36 AptDaemon [DEBUG]: Checking for inactivity
15:35:36 AptDaemon [DEBUG]: Checking for inactivity
15:36:36 AptDaemon [DEBUG]: Checking for inactivity
15:36:36 AptDaemon [INFO]: Quitting due to inactivity
15:36:36 AptDaemon [INFO]: Quitting was requested
15:36:36 AptDaemon [DEBUG]: Quitting main loop...
15:36:36 AptDaemon [DEBUG]: Exit


I think I need to back up my evolution emails and then revert to my old dotfiles if I can't find the ones causing this.

I'm seriously thinking of dumping Ubuntu after this and a number of other instabilities, and go back to using straight Debian again. I used Debian from 1996 until a few years ago when I switched to Ubuntu. Ubuntu has proven to be not any where as stable as Debian always has.

Helen x

---

### Post by dino99 on 2012-03-12
might be a borked index

sudo rm /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get autoclean

sudo apt-get update
sudo apt-get install  -f

sudo dpkg-reconfigure -phigh -a
(be patient, can take a while)

---

### Post by topnaught on 2012-03-12
I had similar problems with Synaptic and the Ubuntu Software Center after a recent update (xubuntu 11.10).

The procedure described by Dino99 corrected the issue: > **dino99 said:**
> might be a borked index

sudo rm /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get autoclean

sudo apt-get update
sudo apt-get install  -f

sudo dpkg-reconfigure -phigh -a
(be patient, can take a while)

---

### Post by Jonners59 on 2012-03-12
> **Helen McCall said:**
> 
I'm seriously thinking of dumping Ubuntu after this and a number of other instabilities, and go back to using straight Debian again. I used Debian from 1996 until a few years ago when I switched to Ubuntu. Ubuntu has proven to be not any where as stable as Debian always has.

Helen x
I am beginning to feel the same....  I am getting frustrated too.

Did this fix your problem?

I have just found that synaptic won't open after I put in my password.  Evolution always starts with the setup screen, and all this after a load of other stuff I spent the WE and today trying to resolve.  This may be a fix for my probs.

---

### Post by Jonners59 on 2012-03-13
I tried this on mine to fix my Synaptics not loading and it failed to work.  Also the first cmd did not work either [HTML]sudo rm /var/lib/apt/lists/*[/HTML] said it was a directory and could not be deleted.

---

### Post by Andrew_P on 2012-03-13
> **Jonners59 said:**
> I tried this on mine to fix my Synaptics not loading and it failed to work.  Also the first cmd did not work either [HTML]sudo rm /var/lib/apt/lists/*[/HTML] said it was a directory and could not be deleted.
It doesn't remove the /partial subdirectory.  However, the "rm" command does clean out everything else in /var/lib/apt/lists, and that's all that's needed.

---

### Post by Helen McCall on 2012-03-13
No it didn't work for me either! :(

Here is the output from the dpkg-reconfigure command:

helen@helen-GA-A75-D3H:~$ sudo dpkg-reconfigure -phigh -a
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Rather than invoking init scripts through /etc/init.d, use the service( 
utility, e.g. service acpid stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(  utility, e.g. stop acpid
acpid stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service( 
utility, e.g. service acpid start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(  utility, e.g. start acpid
acpid start/running, process 5791
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
Rather than invoking init scripts through /etc/init.d, use the service( 
utility, e.g. service apport stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(  utility, e.g. stop apport
Rather than invoking init scripts through /etc/init.d, use the service( 
utility, e.g. service apport start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(  utility, e.g. start apport
start: Job failed to start
invoke-rc.d: initscript apport, action "start" failed.
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
dpkg-trigger: error: must be called from a maintainer script (or with a --by-package option)

---

### Post by Helen McCall on 2012-03-13
I've been looking at the output above and following it all up. The only conclusion I cn make is that the package maintenance system with dpkg and apt appears to be badly broken in this release of Ubuntu 11.10 amd64 - especially because others appear to be experiencing the same problem.

---

### Post by raja.genupula on 2012-03-14
> **Jonners59 said:**
> I tried this on mine to fix my Synaptics not loading and it failed to work.  Also the first cmd did not work either [HTML]sudo rm /var/lib/apt/lists/*[/HTML] said it was a directory and could not be deleted.


are you fine with terminal ? 

actually the command is 
```
sudo rm -rf /var/lib/apt/lists/*
```

after doing that do this 
```
sudo apt-get update 

```
what its giving to you let us know . all the best

---

### Post by Helen McCall on 2012-03-14
Hi Raja,

Ok you asked for the output of that update. So here is my total output.

I hope you can help with this because it is the first problem with Apt or dpkg I've been unable to solve in 16 years of using Debian based systems.

```
helen@helen-GA-A75-D3H:~$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for helen: 
helen@helen-GA-A75-D3H:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric InRelease                             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports InRelease                   
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease [7,096 B]                
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release.gpg [198 B]                 
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [40.8 kB]            
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9,759 B]                       
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release.gpg [198 B]       
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release [40.8 kB]                   
Get:10 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free amd64 Packages [3,219 B]     
Get:11 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources [1,662 B]                 
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources [34.5 kB]      
Get:13 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages [2,477 B]          
Get:14 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [2,477 B]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Get:15 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free amd64 Packages [5,880 B] 
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release [40.8 kB]          
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release [40.8 kB]        
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [14 B]   
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [12.6 kB]  
Get:20 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages [3,215 B]      
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Sources [877 kB]              
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [1,654 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages [90.2 kB]
Get:24 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages [6,418 B]  
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages [14 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages [30.6 kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB                    
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages [3,194 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [90.4 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex            
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [30.6 kB]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [3,362 B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [50.7 kB]
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en [1,494 B]
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en [14 B]
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en [21.6 kB]
Get:40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Sources [5,351 B]       
Get:41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Sources [4,677 kB]        
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_GB               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en
Get:42 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]    
Get:43 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Sources [149 kB]
Get:44 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main amd64 Packages [1,226 kB]     
Get:45 [http://dl.google.com](http://dl.google.com) stable Release [1,338 B]                           
Get:46 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted amd64 Packages [8,261 B]
Get:47 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe amd64 Packages [4,460 kB] 
Get:48 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse amd64 Packages [117 kB] 
Get:49 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main i386 Packages [1,226 kB]      
Get:50 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted i386 Packages [8,216 B] 
Get:51 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe i386 Packages [4,468 kB]  
Get:52 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [469 B]                 
Get:53 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse i386 Packages [119 kB]  
Get:54 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main TranslationIndex [3,289 B]    
Get:55 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse TranslationIndex [2,265 B]
Get:56 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted TranslationIndex [2,263 B]
Get:57 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe TranslationIndex [2,640 B]
Get:58 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Sources [130 kB]      
Get:59 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Sources [1,337 B]
Get:60 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Sources [46.9 kB] 
Get:61 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Sources [3,648 B]
Get:62 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main amd64 Packages [298 kB]
Get:63 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages [2,982 B]
Get:64 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe amd64 Packages [102 kB]
Get:65 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages [6,202 B]
Get:66 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main i386 Packages [299 kB]
Get:67 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,968 B]
Get:68 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe i386 Packages [103 kB]
Get:69 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6,359 B]
Get:70 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]
Get:71 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:72 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:73 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:74 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Sources [2,742 B]
Get:75 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Sources [14 B]
Get:76 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Sources [7,387 B]
Get:77 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Sources [14 B]
Get:78 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main amd64 Packages [3,288 B]
Get:79 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages [14 B]
Get:80 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe amd64 Packages [8,724 B]
Get:81 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages [14 B]
Get:82 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main i386 Packages [3,296 B]
Get:83 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted i386 Packages [14 B]
Get:84 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe i386 Packages [8,701 B]
Get:85 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages [14 B]
Get:86 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main TranslationIndex [72 B]
Get:87 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex [70 B]
Get:88 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex [70 B]
Get:89 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe TranslationIndex [72 B]
Get:90 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en_GB [69.0 kB]
Get:91 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en [701 kB]       
Get:92 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en_GB [68.5 kB]
Get:93 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en [92.6 kB]
Get:94 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en_GB [1,937 B]
Get:95 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en [2,229 B]
Get:96 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en_GB [4,365 B]
Get:97 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en [3,165 kB] 
Get:98 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Translation-en [141 kB]
Get:99 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Translation-en [3,524 B]
Get:100 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Translation-en [508 B]
Get:101 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Translation-en [61.8 kB]
Get:102 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Translation-en [2,292 B]
Get:103 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Translation-en [14 B]
Get:104 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Translation-en [14 B]
Get:105 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Translation-en [6,955 B]
Get:106 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [464 B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Fetched 23.3 MB in 53s (435 kB/s)
Reading package lists... Done
helen@helen-GA-A75-D3H:~$ 


Best wishes, Helen x
```

---

### Post by nothingspecial on 2012-03-14
Hi Helen,

When you post terminal output to the forums, please put it in code tags. The easiest way to do this is to highlight the text then click the # in the formatting options at the top of the posting box.

Thanks.

---

### Post by Helen McCall on 2012-03-14
Thanks for that nothingspecial. The interface for this forum repy box is horribly confusing with so many things all to do with smiliys I don't want. So I missed the hash button for code tags despite looking for a way of doing that.

Best wishes, Helen x

---

### Post by cortman on 2012-03-14
Looks like apt-get update ran flawlessly. Are you still having any problems?

---

### Post by Helen McCall on 2012-03-14
Hi Cortman,

Yes it will still not run synaptic.

I had tried this apt-get update originally before posting here because I expected it to work.

This is what happens when I launch synaptic from a console - both with and without admin privileges:
```

helen@helen-GA-A75-D3H:~$ synaptic
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Aborted
helen@helen-GA-A75-D3H:~$ sudo synaptic
[sudo] password for helen: 
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check

```This is the first time I've been unable to solve a dpkg/apt problem in 16 years of using Debian based systems.

---

### Post by Jonners59 on 2012-03-14
> **Andrew_P said:**
> It doesn't remove the /partial subdirectory.  However, the "rm" command does clean out everything else in /var/lib/apt/lists, and that's all that's needed.
Thanks Andrew
I didn't realise.  I am having the same issue as Helen so I am going to try all she does, as this progresses.  I also have the same issue with Evolution....

PS: My apt-get out put, which I too found flawless - first upgrade to be so for a couple of years.  I normally have an error or two, but this is fine as you can see.

```
$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for baronipc: 
baronipc@baronipc:~$ sudo apt-get update
Ign http://security.ubuntu.com oneiric-security InRelease                      
Get:1 http://security.ubuntu.com oneiric-security Release.gpg [198 B]          
Get:2 http://security.ubuntu.com oneiric-security Release [40.8 kB]            
Get:3 http://security.ubuntu.com oneiric-security/restricted Sources [14 B]    
Get:4 http://security.ubuntu.com oneiric-security/main Sources [34.5 kB]       
Ign https://private-ppa.launchpad.net oneiric InRelease                        
Get:5 http://security.ubuntu.com oneiric-security/multiverse Sources [1,654 B] 
Get:6 http://security.ubuntu.com oneiric-security/universe Sources [12.6 kB]   
Get:7 http://security.ubuntu.com oneiric-security/main amd64 Packages [90.2 kB]
Ign https://private-ppa.launchpad.net maverick InRelease                       
Get:8 http://security.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]
Get:9 http://security.ubuntu.com oneiric-security/universe amd64 Packages [30.6 kB]
Get:10 http://security.ubuntu.com oneiric-security/multiverse amd64 Packages [3,194 B]
Get:11 http://security.ubuntu.com oneiric-security/main i386 Packages [90.4 kB]
Get:12 http://security.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:13 http://security.ubuntu.com oneiric-security/universe i386 Packages [30.6 kB]
Get:14 https://private-ppa.launchpad.net oneiric Release.gpg [316 B]           
Get:15 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [3,362 B]
Get:16 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B]
Get:17 http://security.ubuntu.com oneiric-security/multiverse TranslationIndex [72 B]
Get:18 http://security.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]
Get:19 http://security.ubuntu.com oneiric-security/universe TranslationIndex [73 B]
Get:20 https://private-ppa.launchpad.net maverick Release.gpg [316 B]          
Get:21 http://security.ubuntu.com oneiric-security/main Translation-en [50.7 kB]
Get:22 https://private-ppa.launchpad.net oneiric Release [9,770 B]             
Ign http://archive.canonical.com oneiric InRelease                             
Get:23 http://security.ubuntu.com oneiric-security/multiverse Translation-en [1,494 B]
Get:24 http://security.ubuntu.com oneiric-security/restricted Translation-en [14 B]
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:25 http://security.ubuntu.com oneiric-security/universe Translation-en [21.6 kB]
Get:26 http://archive.canonical.com oneiric Release.gpg [198 B]                
Get:27 https://private-ppa.launchpad.net maverick Release [9,769 B]            
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:28 http://ppa.launchpad.net oneiric Release.gpg [316 B]                    
Get:29 http://archive.canonical.com oneiric Release [5,922 B]                  
Get:30 http://ppa.launchpad.net oneiric Release.gpg [316 B]                    
Get:31 http://ppa.launchpad.net oneiric Release.gpg [316 B]                    
Get:32 https://private-ppa.launchpad.net oneiric/main amd64 Packages [781 B]   
Get:33 http://ppa.launchpad.net oneiric Release.gpg [316 B]                    
Get:34 http://ppa.launchpad.net oneiric Release.gpg [316 B]                    
Get:35 http://ppa.launchpad.net oneiric Release.gpg [316 B]                    
Get:36 http://archive.canonical.com oneiric/partner Sources [2,284 B]          
Get:37 https://private-ppa.launchpad.net oneiric/main i386 Packages [941 B]    
Get:38 http://ppa.launchpad.net oneiric Release [9,742 B]                      
Get:39 http://archive.canonical.com oneiric/partner amd64 Packages [3,073 B]   
Get:40 http://archive.canonical.com oneiric/partner i386 Packages [3,935 B]    
Ign https://private-ppa.launchpad.net oneiric/main TranslationIndex            
Get:41 http://ppa.launchpad.net oneiric Release [9,754 B]                      
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:42 http://ppa.launchpad.net oneiric Release [9,781 B]                      
Get:43 http://ppa.launchpad.net oneiric Release [9,736 B]                      
Get:44 http://ppa.launchpad.net oneiric Release [9,735 B]                      
Get:45 http://ppa.launchpad.net oneiric Release [9,747 B]                      
Get:46 http://ppa.launchpad.net oneiric/main Sources [509 B]                   
Get:47 http://ppa.launchpad.net oneiric/main amd64 Packages [514 B]            
Get:48 http://ppa.launchpad.net oneiric/main i386 Packages [514 B]             
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:49 http://ppa.launchpad.net oneiric/main Sources [1,210 B]                 
Get:50 http://ppa.launchpad.net oneiric/main amd64 Packages [1,502 B]          
Get:51 http://ppa.launchpad.net oneiric/main i386 Packages [1,489 B]           
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:52 http://ppa.launchpad.net oneiric/main Sources [707 B]                   
Get:53 http://ppa.launchpad.net oneiric/main amd64 Packages [732 B]            
Get:54 https://private-ppa.launchpad.net maverick/main amd64 Packages [1,068 B]
Get:55 http://ppa.launchpad.net oneiric/main i386 Packages [739 B]             
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:56 http://ppa.launchpad.net oneiric/main Sources [1,182 B]                 
Get:57 http://ppa.launchpad.net oneiric/main amd64 Packages [1,202 B]          
Get:58 http://ppa.launchpad.net oneiric/main i386 Packages [1,202 B]           
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:59 http://ppa.launchpad.net oneiric/main Sources [751 B]                   
Get:60 http://ppa.launchpad.net oneiric/main amd64 Packages [1,344 B]          
Get:61 http://ppa.launchpad.net oneiric/main i386 Packages [1,359 B]           
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:62 http://ppa.launchpad.net oneiric/main Sources [543 B]                   
Get:63 http://ppa.launchpad.net oneiric/main amd64 Packages [642 B]            
Get:64 http://ppa.launchpad.net oneiric/main i386 Packages [642 B]             
Get:65 https://private-ppa.launchpad.net maverick/main i386 Packages [1,221 B] 
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign https://private-ppa.launchpad.net maverick/main TranslationIndex           
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://gb.archive.ubuntu.com oneiric InRelease                             
Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://gb.archive.ubuntu.com oneiric-backports InRelease                   
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://extras.ubuntu.com oneiric InRelease                                 
Get:66 http://gb.archive.ubuntu.com oneiric Release.gpg [198 B]                
Get:67 http://gb.archive.ubuntu.com oneiric-updates Release.gpg [198 B]        
Get:68 http://gb.archive.ubuntu.com oneiric-backports Release.gpg [198 B]      
Get:69 http://extras.ubuntu.com oneiric Release.gpg [72 B]                     
Get:70 http://gb.archive.ubuntu.com oneiric Release [40.8 kB]                  
Get:71 http://extras.ubuntu.com oneiric Release [9,759 B]                      
Get:72 http://gb.archive.ubuntu.com oneiric-updates Release [40.8 kB]          
Get:73 http://gb.archive.ubuntu.com oneiric-backports Release [40.8 kB]        
Get:74 http://extras.ubuntu.com oneiric/main Sources [1,662 B]                 
Get:75 http://gb.archive.ubuntu.com oneiric/restricted Sources [5,351 B]       
Get:76 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]              
Get:77 http://extras.ubuntu.com oneiric/main amd64 Packages [2,477 B]          
Get:78 http://extras.ubuntu.com oneiric/main i386 Packages [2,477 B]           
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Ign http://download.ebz.epson.net lsb3.2 InRelease                             
Get:79 http://download.ebz.epson.net lsb3.2 Release.gpg [189 B]                
Get:80 http://download.ebz.epson.net lsb3.2 Release [86.9 kB]                  
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Get:81 http://download.ebz.epson.net lsb3.2/main amd64 Packages [9,044 B]      
Get:82 http://download.ebz.epson.net lsb3.2/main i386 Packages [9,125 B]       
Ign http://download.ebz.epson.net lsb3.2/main TranslationIndex                 
Get:83 http://gb.archive.ubuntu.com oneiric/multiverse Sources [149 kB]        
Get:84 http://gb.archive.ubuntu.com oneiric/universe Sources [4,677 kB]        
Ign http://archive.ubuntu.com oneiric InRelease                                
Get:85 http://archive.ubuntu.com oneiric Release.gpg [198 B]                   
Get:86 http://archive.ubuntu.com oneiric Release [40.8 kB]                     
Get:87 http://archive.ubuntu.com oneiric/main Sources [877 kB]                 
Ign http://download.ebz.epson.net lsb3.2/main Translation-en_GB                
Ign http://download.ebz.epson.net lsb3.2/main Translation-en                   
Get:88 http://archive.ubuntu.com oneiric/restricted Sources [5,351 B]          
Ign https://private-ppa.launchpad.net oneiric/main Translation-en_GB           
Ign https://private-ppa.launchpad.net oneiric/main Translation-en              
Ign https://private-ppa.launchpad.net maverick/main Translation-en_GB          
Ign https://private-ppa.launchpad.net maverick/main Translation-en             
Get:89 http://gb.archive.ubuntu.com oneiric/main amd64 Packages [1,226 kB]     
Get:90 http://gb.archive.ubuntu.com oneiric/restricted amd64 Packages [8,261 B]
Get:91 http://gb.archive.ubuntu.com oneiric/universe amd64 Packages [4,460 kB] 
Get:92 http://gb.archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB] 
Get:93 http://gb.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]      
Get:94 http://gb.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B] 
Get:95 http://gb.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]  
Get:96 http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]  
Get:97 http://gb.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]    
Get:98 http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]
Get:99 http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]
Get:100 http://gb.archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]
Get:101 http://gb.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]
Get:102 http://gb.archive.ubuntu.com oneiric-updates/main Sources [130 kB]     
Get:103 http://gb.archive.ubuntu.com oneiric-updates/multiverse Sources [3,648 B]
Get:104 http://gb.archive.ubuntu.com oneiric-updates/universe Sources [47.2 kB]
Get:105 http://gb.archive.ubuntu.com oneiric-updates/main amd64 Packages [298 kB]
Get:106 http://gb.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]
Get:107 http://gb.archive.ubuntu.com oneiric-updates/universe amd64 Packages [102 kB]
Get:108 http://gb.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,202 B]
Get:109 http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages [299 kB]
Get:110 http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:111 http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages [103 kB]
Get:112 http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,359 B]
Get:113 http://gb.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:114 http://gb.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:115 http://gb.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:116 http://gb.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Get:117 http://gb.archive.ubuntu.com oneiric-backports/main Sources [2,742 B]  
Get:118 http://gb.archive.ubuntu.com oneiric-backports/restricted Sources [14 B]
Get:119 http://gb.archive.ubuntu.com oneiric-backports/universe Sources [7,387 B]
Get:120 http://gb.archive.ubuntu.com oneiric-backports/multiverse Sources [14 B]
Get:121 http://gb.archive.ubuntu.com oneiric-backports/main amd64 Packages [3,288 B]
Get:122 http://gb.archive.ubuntu.com oneiric-backports/restricted amd64 Packages [14 B]
Get:123 http://gb.archive.ubuntu.com oneiric-backports/universe amd64 Packages [8,724 B]
Get:124 http://gb.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages [14 B]
Get:125 http://gb.archive.ubuntu.com oneiric-backports/main i386 Packages [3,296 B]
Get:126 http://gb.archive.ubuntu.com oneiric-backports/restricted i386 Packages [14 B]
Get:127 http://gb.archive.ubuntu.com oneiric-backports/universe i386 Packages [8,701 B]
Get:128 http://gb.archive.ubuntu.com oneiric-backports/multiverse i386 Packages [14 B]
Get:129 http://gb.archive.ubuntu.com oneiric-backports/main TranslationIndex [72 B]
Get:130 http://gb.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex [70 B]
Get:131 http://gb.archive.ubuntu.com oneiric-backports/restricted TranslationIndex [70 B]
Get:132 http://gb.archive.ubuntu.com oneiric-backports/universe TranslationIndex [72 B]
Get:133 http://gb.archive.ubuntu.com oneiric/main Translation-en_GB [69.0 kB]  
Get:134 http://gb.archive.ubuntu.com oneiric/main Translation-en [701 kB]      
Get:135 http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB [68.5 kB]
Get:136 http://gb.archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]
Get:137 http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB [1,937 B]
Get:138 http://gb.archive.ubuntu.com oneiric/restricted Translation-en [2,229 B]
Get:139 http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB [4,365 B]
Get:140 http://gb.archive.ubuntu.com oneiric/universe Translation-en [3,165 kB]
Get:141 http://gb.archive.ubuntu.com oneiric-updates/main Translation-en [141 kB]
Get:142 http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en [3,524 B]
Get:143 http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en [508 B]
Get:144 http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en [61.9 kB]
Get:145 http://gb.archive.ubuntu.com oneiric-backports/main Translation-en [2,292 B]
Get:146 http://gb.archive.ubuntu.com oneiric-backports/multiverse Translation-en [14 B]
Get:147 http://gb.archive.ubuntu.com oneiric-backports/restricted Translation-en [14 B]
Get:148 http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en [6,955 B]
Fetched 24.4 MB in 1min 10s (348 kB/s)                                         
Reading package lists... Done

```

Trying synaptic in Terminal:
without sudo
```
$ synaptic

(synaptic:3244): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Aborted

```

with sudo
```
$ sudo synaptic

(synaptic:3253): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
```

Does any of this help?

---

### Post by cortman on 2012-03-14
Hi Helen/Jonners,

Have either of you tried uninstalling/reinstalling Synaptic?

```
sudo apt-get purge synaptic
sudo apt-get install synaptic
```

---

### Post by Jonners59 on 2012-03-14
> **cortman said:**
> Hi Helen/Jonners,

Have either of you tried uninstalling/reinstalling Synaptic?

```
sudo apt-get purge synaptic
sudo apt-get install synaptic
```

Funny, I thought the same, but normally when I remove an app I use Synaptic.  Had no idea how to do via cmd... any how, I have tried and it still fails.

Another idea...

---

### Post by Helen McCall on 2012-03-14
> **cortman said:**
> Hi Helen/Jonners,

Have either of you tried uninstalling/reinstalling Synaptic?

```
sudo apt-get purge synaptic
sudo apt-get install synaptic
```

> **Jonners59 said:**
> Funny, I thought  the same, but normally when I remove an app I use Synaptic.  Had no  idea how to do via cmd... any how, I have tried and it still fails.

Another idea... 	  	

I had thought of reinstalling synaptic, but I checked the synaptic package files as listed by dpkg and found it hadn't been altered at all, and so I didn't re-install it.

I also checked for likely lock files but didn't find any.

---

### Post by matt_symes on 2012-03-14
Hi

Does this help ?

[http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing](http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing)

Kind regards

---

### Post by Helen McCall on 2012-03-14
Thank you Matt :p

That has fixed the synaptic problem. 

The bug must have been activated when I tried out the accessibility options for text to speech. I hope this accessibility bug is fixed soon.

For those who need a quick answer:

go to System Settings->Universal Access and change any of the settings and then change them back to what they were. Then synaptic will run properly again.

Thank you again Matt. It is quite a coincidence that I got the answer from someone in Bristol. I'm a Professional Member of Circomedia in Bristol. I'm the oldest professional woman aerialist in British circus.

Best wishes, Helen x

---

### Post by matt_symes on 2012-03-14
Hi

> It is quite a coincidence that I got the answer from someone in Bristol. I'm a Professional Member of Circomedia in Bristol. I'm the oldest professional woman aerialist in British circus.

Then the pleasure is all mine :)

I just passed on the link though.

Kind regards

---

### Post by Jonners59 on 2012-03-14
Excellent.  WOrked for me too, bar one addition.  I had to do a reboot after making the changes.  I then changed the settings back as soon as I had logged back in.

Thank Matt and everyone else who contributed, and Helen for letting me hitch hick her thread.

Right just stunnel and Evolution to sort out now!

---

### Post by ian2k5 on 2012-04-08
Thank you, Matt,
It worked like a charm for me. I had no idea going into Universal Access and enabling Screen Reader, then disabling it, would allow me to get Synaptic back up and running. Before doing the above-mentioned, all I got was a Synaptic window for about two seconds, and then nothing.
Thank you so much for the help and posting the link.

---

