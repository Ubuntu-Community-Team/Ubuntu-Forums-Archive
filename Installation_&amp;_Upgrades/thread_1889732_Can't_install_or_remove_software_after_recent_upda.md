---
title: "Can't install or remove software after recent update"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by yellowcrash10 on 2011-12-01
Hello! I'm having a problem after updating things from the Update Manager. I can't install any new software from the Ubuntu Software Center, and Update Manager seems to be the problem. I'll attach an image of the Software Center dialog, but here is the output from Terminal when I run 'apt-get -f install':
```
root@ubuntu:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libglade2-0 libreoffice-common thunderbird
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-tango
  libreoffice-style-crystal libreoffice-style-oxygen latex-xft-fonts
The following NEW packages will be installed:
  libglade2-0
The following packages will be upgraded:
  libreoffice-common thunderbird
2 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
16 not fully installed or removed.
Need to get 54.1 kB/36.8 MB of archives.
After this operation, 1,180 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric/main libglade2-0 amd64 1:2.6.4-1build1 [54.1 kB]
Fetched 54.1 kB in 0s (57.9 kB/s)      
Selecting previously deselected package libglade2-0.
(Reading database ... 156141 files and directories currently installed.)
Unpacking libglade2-0 (from .../libglade2-0_1%3a2.6.4-1build1_amd64.deb) ...
Preparing to replace libreoffice-common 1:3.4.3-3ubuntu2 (using .../libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb) ...
Unpacking replacement libreoffice-common ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
xz: (stdin): Unexpected end of input
dpkg-deb: error: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libreoffice/basis3.4/share/xslt/import/spreadsheetml/spreadsheetml2ooo.xsl'
Preparing to replace thunderbird 7.0.1+build1+nobinonly-0ubuntu1 (using .../thunderbird_8.0+build1-0ubuntu0.11.10.1_amd64.deb) ...
Unpacking replacement thunderbird ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/thunderbird_8.0+build1-0ubuntu0.11.10.1_amd64.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/thunderbird-8.0/libxul.so'
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb
 /var/cache/apt/archives/thunderbird_8.0+build1-0ubuntu0.11.10.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I was running it as root, but it shows the same thing when I type it in a terminal under my user.
I'm not sure if this will help, but I'll include a screenshot of the Authentication tab in Software Sources window in case the keys are the problem.

---

### Post by zvacet on 2011-12-03
```
sudo dpkg --configure -a
```

---

### Post by yellowcrash10 on 2011-12-03
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

I tried what you said and it threw up a bunch of errors. Here's the output:
```
corin@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for corin: 
dpkg: dependency problems prevent configuration of thunderbird-globalmenu:
 thunderbird-globalmenu depends on thunderbird (= 8.0+build1-0ubuntu0.11.10.1); however:
  Version of thunderbird on system is 7.0.1+build1+nobinonly-0ubuntu1.
dpkg: error processing thunderbird-globalmenu (--configure):
 dependency problems - leaving unconfigured
Setting up libglade2-0 (1:2.6.4-1build1) ...
dpkg: dependency problems prevent configuration of thunderbird-gnome-support:
 thunderbird-gnome-support depends on thunderbird (= 8.0+build1-0ubuntu0.11.10.1); however:
  Version of thunderbird on system is 7.0.1+build1+nobinonly-0ubuntu1.
dpkg: error processing thunderbird-gnome-support (--configure):
 dependency problems - leaving unconfigured
Setting up hamachi-gui (0.9.5-0) ...
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libreoffice-common (>> 1:3.4.4); however:
  Version of libreoffice-common on system is 1:3.4.3-3ubuntu2.
dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-style-human:
 libreoffice-style-human depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-emailmerge:
 libreoffice-emailmerge depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gtk:
 libreoffice-gtk depends on libreoffice-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on libreoffice-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libreoffice-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-help-en-us:
 libreoffice-help-en-us depends on libreoffice-writer | language-support-translations-en; however:
  Package libreoffice-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing libreoffice-help-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
 libreoffice-calc depends on libreoffice-base-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-base-core is not configured yet.
dpkg: error processing libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 thunderbird-globalmenu
 thunderbird-gnome-support
 libreoffice-core
 libreoffice-style-human
 libreoffice-math
 libreoffice-impress
 libreoffice-writer
 libreoffice-base-core
 libreoffice-gnome
 libreoffice-emailmerge
 libreoffice-gtk
 python-uno
 libreoffice-draw
 libreoffice-help-en-us
 libreoffice-calc
corin@ubuntu:~$ 

```

---

### Post by bluexrider on 2011-12-03
remove the packages and reinstall

sudo rm /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb  

sudo rm /var/cache/apt/archives/thunderbird_8.0+build1-0ubuntu0.11.10.1_amd64.deb

sudo apt-get clean

sudo apt-get update && sudo apt-get upgrade

---

### Post by yellowcrash10 on 2011-12-03
> **bluexrider said:**
> remove the packages and reinstall

sudo rm /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb  

sudo rm /var/cache/apt/archives/thunderbird_8.0+build1-0ubuntu0.11.10.1_amd64.deb

sudo apt-get clean

sudo apt-get update && sudo apt-get upgrade

I tried this and it didn't seem to work at the "sudo apt-get update && sudo apt-get upgrade" part. Here's the output:
```
corin@ubuntu:~$ sudo rm /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb 
[sudo] password for corin: 
corin@ubuntu:~$ sudo rm /var/cache/apt/archives/thunderbird_8.0+build1-0ubuntu0.11.10.1_amd64.deb
corin@ubuntu:~$ sudo apt-get clean
corin@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
Ign http://archive.canonical.com oneiric InRelease
Ign http://security.ubuntu.com oneiric-security InRelease           
Ign http://archive.ubuntu.com oneiric InRelease                      
Ign http://archive.ubuntu.com oneiric-updates InRelease              
Hit http://archive.canonical.com oneiric Release.gpg                 
Get:1 http://security.ubuntu.com oneiric-security Release.gpg [198 B]
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Hit http://archive.canonical.com oneiric Release                     
Get:2 http://security.ubuntu.com oneiric-security Release [32.4 kB]            
Get:3 http://archive.ubuntu.com oneiric-updates Release.gpg [198 B]            
Ign http://dl.google.com stable InRelease                                      
Get:4 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://archive.ubuntu.com oneiric Release                                  
Get:5 http://dl.google.com stable Release [1,347 B]                            
Get:6 http://dl.google.com stable/main amd64 Packages [1,234 B]                
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Get:7 http://archive.ubuntu.com oneiric-updates Release [32.4 kB]              
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:8 http://security.ubuntu.com oneiric-security/main amd64 Packages [54.7 kB]
Get:9 http://dl.google.com stable/main i386 Packages [1,207 B]                 
Hit http://archive.ubuntu.com oneiric/main amd64 Packages                      
Hit http://archive.ubuntu.com oneiric/restricted amd64 Packages                
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages                  
Hit http://archive.ubuntu.com oneiric/multiverse amd64 Packages                
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages                 
Hit http://archive.ubuntu.com oneiric/main TranslationIndex                    
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Ign http://dl.google.com stable/main TranslationIndex                          
Get:10 http://security.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]
Get:11 http://security.ubuntu.com oneiric-security/universe amd64 Packages [15.5 kB]
Get:12 http://security.ubuntu.com oneiric-security/multiverse amd64 Packages [919 B]
Get:13 http://security.ubuntu.com oneiric-security/main i386 Packages [54.8 kB]
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex                
Get:14 http://archive.ubuntu.com oneiric-updates/main amd64 Packages [217 kB]  
Get:15 http://security.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:16 http://security.ubuntu.com oneiric-security/universe i386 Packages [15.5 kB]
Get:17 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [1,653 B]
Get:18 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B]
Get:19 http://security.ubuntu.com oneiric-security/multiverse TranslationIndex [71 B]
Get:20 http://security.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]
Get:21 http://security.ubuntu.com oneiric-security/universe TranslationIndex [73 B]
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Get:22 http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,966 B]
Ign http://archive.canonical.com oneiric/partner Translation-en                
Get:23 http://archive.ubuntu.com oneiric-updates/universe amd64 Packages [56.9 kB]
Ign http://dl.google.com stable/main Translation-en_US                        
Get:24 http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [3,763 B]
Get:25 http://archive.ubuntu.com oneiric-updates/main i386 Packages [218 kB]   
Ign http://dl.google.com stable/main Translation-en                            
Get:26 http://archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,935 B]
Get:27 http://archive.ubuntu.com oneiric-updates/universe i386 Packages [57.2 kB]
Get:28 http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages [4,396 B]
Get:29 http://archive.ubuntu.com oneiric-updates/main TranslationIndex [73 B]  
Get:30 http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:31 http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:32 http://archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://archive.ubuntu.com oneiric/main Translation-en                      
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en                
Hit http://archive.ubuntu.com oneiric/restricted Translation-en                
Hit http://archive.ubuntu.com oneiric/universe Translation-en                  
Get:33 http://archive.ubuntu.com oneiric-updates/main Translation-en [99.2 kB] 
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en          
Fetched 876 kB in 7s (122 kB/s)                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:3.4.4) but 1:3.4.3-3ubuntu2 is installed
 thunderbird-globalmenu : Depends: thunderbird (= 8.0+build1-0ubuntu0.11.10.1) but 7.0.1+build1+nobinonly-0ubuntu1 is installed
 thunderbird-gnome-support : Depends: thunderbird (= 8.0+build1-0ubuntu0.11.10.1) but 7.0.1+build1+nobinonly-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.
corin@ubuntu:~$ 

```

Thanks for all the help so far! :)

---

### Post by oldtimer7777 on 2011-12-03
> **bluexrider said:**
> remove the packages and reinstall

sudo rm /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb  

sudo rm /var/cache/apt/archives/thunderbird_8.0+build1-0ubuntu0.11.10.1_amd64.deb

sudo apt-get clean

sudo apt-get update && sudo apt-get upgrade

Also make sure to clean out your system completely before you attempt a reinstallation of anything else. 

And also install from PPAs when possible.

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

To clean your system

sudo apt-get install bleachbit
sudo bleachbit

---

### Post by yellowcrash10 on 2011-12-03
I can install software again! :D
Thanks to everyone that helped!

---

### Post by bluexrider on 2011-12-03
> **yellowcrash10 said:**
> I can install software again! :D
Thanks to everyone that helped!

Yes, you can reinstall it all. Fairly simple.

Happy *buntu

please mark this (SOLVED)

---

### Post by yellowcrash10 on 2011-12-07
Ok, I figured out how to make it solved. Thanks again  for all the help!

---

