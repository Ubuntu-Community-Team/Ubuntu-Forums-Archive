---
title: "Can't install flash player"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by evil gnome on 2012-02-23
```
xxx@xxx-desktop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'flashplugin-downloader' instead of 'flashplugin-nonfree'
flashplugin-downloader is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up flashplugin-downloader (11.0.1.152ubuntu1) ...
Downloading...
--2012-02-23 14:47:11--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Resolving archive.canonical.com... 91.189.92.191, 91.189.88.33
Connecting to archive.canonical.com|91.189.92.191|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-23 14:47:12 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 flashplugin-downloader
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm running Lubuntu 11.10

---

### Post by winh8r on 2012-02-23
try having a look at this thread, solves most issues with Flash.

hope this helps you.


[http://ubuntuforums.org/showthread.php?t=1491268]("http://ubuntuforums.org/showthread.php?t=1491268")

---

### Post by evil gnome on 2012-02-23
> **winh8r said:**
> try having a look at this thread, solves most issues with Flash.

hope this helps you.


[http://ubuntuforums.org/showthread.php?t=1491268]("http://ubuntuforums.org/showthread.php?t=1491268")
[FONT="Courier New"]Thank you but I forgot to tell I'm using **Chromium** not Firefox[/FONT]

---

### Post by lovinglinux on 2012-02-23
> **evil gnome said:**
> [FONT="Courier New"]Thank you but I forgot to tell I'm using **Chromium** not Firefox[/FONT]

No problem, you can install Flash-Aid on Firefox, execute the Wizard to install flash, then close Firefox. Chromium will detect and use the plugin as well.

---

### Post by ottosykora on 2012-02-23
just curious:

does not chromium come on linux also delivered with its own flash included?


(it does on windows)

---

### Post by evil gnome on 2012-02-23
> **ottosykora said:**
> just curious:

does not chromium come on linux also delivered with its own flash included?


(it does on windows)
[FONT="Courier New"][LIST]
[*]Google Chrome comes with built-in flash player (Doubtful about linux)
[*]Chromium lacks built-in flash player
[/LIST][/FONT]

---

### Post by evil gnome on 2012-02-24
[FONT="Courier New"]PROBLEM SOLVED

The first time I installed Lubuntu, and it was fast and nice, then chose to download all "important security updates", but after that the system became slow and sluggish, and never became fast again no matter how hard I tried (like removing old kernels...).

So I reinstalled Lubuntu, and this time disabled ALL updates. and was wondering what problems might happen because of this. Being unable to install flash was the first one so far. I solved it by updating the following packages:
```
flashplugin-installer
flashplugin-downloader

```

And after that, did run Flash-Aid again from firefox:
```
***************************************************************************
*****************PLEASE WAIT...DON'T CLOSE THIS TERMINAL!******************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting removal commands*************************
***************************************************************************
***************************************************************************
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'flashplugin-installer' for regex 'flashplugin.*installer'
The following packages will be REMOVED:
  flashplugin-downloader* flashplugin-installer*
0 upgraded, 0 newly installed, 2 to remove and 75 not upgraded.
After this operation, 209 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113036 files and directories currently installed.)
Removing flashplugin-downloader ...
Removing flashplugin-installer ...
Purging configuration files for flashplugin-installer ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-downloader is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 75 not upgraded.
***************************************************************************
*************************Starting update commands**************************
***************************************************************************
***************************************************************************
Ign http://archive.canonical.com oneiric InRelease
Ign http://security.ubuntu.com oneiric-security InRelease            
Ign http://extras.ubuntu.com oneiric InRelease                       
Ign http://us.archive.ubuntu.com oneiric InRelease                   
Hit http://archive.canonical.com oneiric Release.gpg                 
Hit http://security.ubuntu.com oneiric-security Release.gpg          
Hit http://archive.canonical.com oneiric Release                     
Hit http://security.ubuntu.com oneiric-security Release              
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://us.archive.ubuntu.com oneiric Release.gpg                 
Hit http://archive.canonical.com oneiric/partner i386 Packages       
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://extras.ubuntu.com oneiric Release                         
Hit http://us.archive.ubuntu.com oneiric Release                               
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://security.ubuntu.com oneiric-security/main i386 Packages   
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en     
Ign http://archive.canonical.com oneiric/partner Translation-en_US   
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Reading package lists... Done
***************************************************************************
*************************Starting install commands*************************
***************************************************************************
***************************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  msttcorefonts ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 75 not upgraded.
Need to get 0 B/9,504 B of archives.
After this operation, 164 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 113013 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.1.102.62ubuntu0.11.10.2_i386.deb) ...
Setting up flashplugin-installer (11.1.102.62ubuntu0.11.10.2) ...
Downloading...
--2012-02-24 10:05:38--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.62.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33, 91.189.92.191
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13785778 (13M) [application/x-gzip]
Saving to: `./adobe-flashplugin_11.1.102.62.orig.tar.gz'

     0K ........ ........ ........ ........ ........ ........ 22% 93.4K 1m51s
  3072K ........ ........ ........ ........ ........ ........ 45% 96.5K 77s
  6144K ........ ........ ........ ........ ........ ........ 68%  105K 43s
  9216K ........ ........ ........ ........ ........ ........ 91%  139K 11s
 12288K ........ ........ ..                                 100%  241K=2m1s

2012-02-24 10:07:39 (111 KB/s) - `./adobe-flashplugin_11.1.102.62.orig.tar.gz' saved [13785778/13785778]

Download done.
Flash Plugin installed.
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************
OverrideGPUValidation=true
***************************************************************************
******FINISHED! You can close this terminal and restart Firefox now.*******
***************************************************************************
***************************************************************************

```

Flash is installed now and working in Chromium.

Thank you **winh8r** for posting the link to Flash-Aid thread.
Thank you **lovinglinux** for developing Flash-Aid and most importantly giving hints about my problem.[/FONT]

---

### Post by lovinglinux on 2012-02-24
> **evil gnome said:**
> [FONT="Courier New"]PROBLEM SOLVED

The first time I installed Lubuntu, and it was fast and nice, then chose to download all "important security updates", but after that the system became slow and sluggish, and never became fast again no matter how hard I tried (like removing old kernels...).

So I reinstalled Lubuntu, and this time disabled ALL updates. and was wondering what problems might happen because of this. Being unable to install flash was the first one so far. I solved it by updating the following packages:
```
flashplugin-installer
flashplugin-downloader

```

And after that, did run Flash-Aid again from firefox:
```
***************************************************************************
*****************PLEASE WAIT...DON'T CLOSE THIS TERMINAL!******************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting removal commands*************************
***************************************************************************
***************************************************************************
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'flashplugin-installer' for regex 'flashplugin.*installer'
The following packages will be REMOVED:
  flashplugin-downloader* flashplugin-installer*
0 upgraded, 0 newly installed, 2 to remove and 75 not upgraded.
After this operation, 209 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113036 files and directories currently installed.)
Removing flashplugin-downloader ...
Removing flashplugin-installer ...
Purging configuration files for flashplugin-installer ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-downloader is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 75 not upgraded.
***************************************************************************
*************************Starting update commands**************************
***************************************************************************
***************************************************************************
Ign http://archive.canonical.com oneiric InRelease
Ign http://security.ubuntu.com oneiric-security InRelease            
Ign http://extras.ubuntu.com oneiric InRelease                       
Ign http://us.archive.ubuntu.com oneiric InRelease                   
Hit http://archive.canonical.com oneiric Release.gpg                 
Hit http://security.ubuntu.com oneiric-security Release.gpg          
Hit http://archive.canonical.com oneiric Release                     
Hit http://security.ubuntu.com oneiric-security Release              
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://us.archive.ubuntu.com oneiric Release.gpg                 
Hit http://archive.canonical.com oneiric/partner i386 Packages       
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://extras.ubuntu.com oneiric Release                         
Hit http://us.archive.ubuntu.com oneiric Release                               
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://security.ubuntu.com oneiric-security/main i386 Packages   
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en     
Ign http://archive.canonical.com oneiric/partner Translation-en_US   
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Reading package lists... Done
***************************************************************************
*************************Starting install commands*************************
***************************************************************************
***************************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  msttcorefonts ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 75 not upgraded.
Need to get 0 B/9,504 B of archives.
After this operation, 164 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 113013 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.1.102.62ubuntu0.11.10.2_i386.deb) ...
Setting up flashplugin-installer (11.1.102.62ubuntu0.11.10.2) ...
Downloading...
--2012-02-24 10:05:38--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.62.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33, 91.189.92.191
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13785778 (13M) [application/x-gzip]
Saving to: `./adobe-flashplugin_11.1.102.62.orig.tar.gz'

     0K ........ ........ ........ ........ ........ ........ 22% 93.4K 1m51s
  3072K ........ ........ ........ ........ ........ ........ 45% 96.5K 77s
  6144K ........ ........ ........ ........ ........ ........ 68%  105K 43s
  9216K ........ ........ ........ ........ ........ ........ 91%  139K 11s
 12288K ........ ........ ..                                 100%  241K=2m1s

2012-02-24 10:07:39 (111 KB/s) - `./adobe-flashplugin_11.1.102.62.orig.tar.gz' saved [13785778/13785778]

Download done.
Flash Plugin installed.
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************
OverrideGPUValidation=true
***************************************************************************
******FINISHED! You can close this terminal and restart Firefox now.*******
***************************************************************************
***************************************************************************

```

Flash is installed now and working in Chromium.

Thank you **winh8r** for posting the link to Flash-Aid thread.
Thank you **lovinglinux** for developing Flash-Aid and most importantly giving hints about my problem.[/FONT]


You are welcome. I am glad you fixed it.

---

### Post by winh8r on 2012-02-24
No problem. Glad to see you have got it running.


Good Luck.

---

