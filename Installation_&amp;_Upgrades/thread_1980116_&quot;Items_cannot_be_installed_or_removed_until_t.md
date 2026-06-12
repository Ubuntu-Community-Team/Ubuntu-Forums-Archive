---
title: "&quot;Items cannot be installed or removed until the package catalog is repaired&quot;"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by duodecillian on 2012-05-14
Clicking repair gives me another error, this happened after I installed Skype. Even trying to fix the broken packages in the synaptic package manager is giving me an error.

I'm sure there's more information you need to help me, so whatever you need I'm more than willing to let you know. Thanks in advance.

---

### Post by oldos2er on 2012-05-14
Can you open a terminal (Ctrl-Alt-t), run the following command, and copy and paste all the output here? ```
sudo apt-get update
```

---

### Post by duodecillian on 2012-05-14
```
duodecillian@ubuntu:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                      
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://archive.canonical.com precise InRelease                             
Ign http://archive.ubuntu.com precise InRelease                      
Ign http://archive.ubuntu.com precise-updates InRelease              
Ign http://security.ubuntu.com precise-security InRelease            
Get:3 http://dl.google.com stable Release [1,347 B]                  
Get:4 http://dl.google.com stable Release [1,347 B]                            
Hit http://archive.canonical.com precise Release.gpg                           
Get:5 http://archive.ubuntu.com precise Release.gpg [198 B]                    
Get:6 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://archive.canonical.com precise Release                               
Get:7 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Get:8 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:9 http://archive.ubuntu.com precise Release [49.6 kB]                      
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:10 http://archive.ubuntu.com precise-updates Release [49.6 kB]             
Get:11 http://security.ubuntu.com precise-security/main amd64 Packages [32.9 kB]
Get:12 http://archive.ubuntu.com precise/main amd64 Packages [1,273 kB]        
Get:13 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:14 http://security.ubuntu.com precise-security/universe amd64 Packages [8,581 B]
Get:15 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,142 B]
Get:16 http://security.ubuntu.com precise-security/main i386 Packages [32.9 kB]
Get:17 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:18 http://security.ubuntu.com precise-security/universe i386 Packages [8,594 B]
Get:19 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,393 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:20 http://dl.google.com stable/main amd64 Packages [1,245 B]               
Get:21 http://dl.google.com stable/main i386 Packages [1,268 B]                
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://archive.canonical.com precise/partner Translation-en_US             
Get:22 http://dl.google.com stable/main amd64 Packages [765 B]                 
Get:23 http://dl.google.com stable/main i386 Packages [769 B]                  
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en        
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Get:24 http://archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:25 http://archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]
Get:26 http://archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]                                                                          
Get:27 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]                                                                               
Get:28 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]                                                                          
Get:29 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]                                                                           
Get:30 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                                                                           
Hit http://archive.ubuntu.com precise/main TranslationIndex                                                                                          
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex                                                                                    
Hit http://archive.ubuntu.com precise/restricted TranslationIndex                                                                                    
Hit http://archive.ubuntu.com precise/universe TranslationIndex                                                                                      
Get:31 http://archive.ubuntu.com precise-updates/main amd64 Packages [95.2 kB]                                                                       
Get:32 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [757 B]                                                                   
Get:33 http://archive.ubuntu.com precise-updates/universe amd64 Packages [27.5 kB]                                                                   
Get:34 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,142 B]                                                                 
Get:35 http://archive.ubuntu.com precise-updates/main i386 Packages [96.5 kB]                                                                        
Get:36 http://archive.ubuntu.com precise-updates/restricted i386 Packages [770 B]                                                                    
Get:37 http://archive.ubuntu.com precise-updates/universe i386 Packages [27.7 kB]                                                                    
Get:38 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [1,393 B]                                                                  
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex                                                                                  
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                            
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                            
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex                                                                              
Hit http://archive.ubuntu.com precise/main Translation-en                                                                                            
Hit http://archive.ubuntu.com precise/multiverse Translation-en                                                                                      
Hit http://archive.ubuntu.com precise/restricted Translation-en                                                                                      
Hit http://archive.ubuntu.com precise/universe Translation-en                                                                                        
Hit http://archive.ubuntu.com precise-updates/main Translation-en                                                                                    
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en                                                                              
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en                                                                              
Hit http://archive.ubuntu.com precise-updates/universe Translation-en 
```

---

### Post by matt_symes on 2012-05-14
Hi

After the update command from oldos2er, i would now run


```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

(I think autoclean might remove a subset of clean but...)

and then


```
sudo apt-get -f install
```
Post back any errors these commands may produce.


If no errors then try to use the software center again.


Kind regards

---

### Post by duodecillian on 2012-05-14
When running the autoremove command I get this:
```
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libdbusmenu-qt2:i386 : Depends: libqtcore4:i386 (>= 4:4.7.0~beta1) but it is not installed
 libqt4-dbus:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.1) but it is not installed
 libqt4-declarative:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.1) but it is not installed
 libqt4-network:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.1) but it is not installed
 libqt4-script:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.1) but it is not installed
 libqt4-sql:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.1) but it is not installed
 libqt4-sql-mysql:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.1) but it is not installed
 libqt4-xml:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.1) but it is not installed
 libqt4-xmlpatterns:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.1) but it is not installed
 libqtgui4:i386 : Depends: libqtcore4:i386 (= 4:4.8.1-0ubuntu4.1) but it is not installed
 skype-bin:i386 : Depends: libqtcore4:i386 (>= 4:4.5.3) but it is not installed
 sni-qt:i386 : Depends: libqtcore4:i386 (>= 4:4.7.3-1ubuntu3~) but it is not installed
E: Unmet dependencies. Try using -f.

```

When running apt-get -f install

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libqtcore4:i386
The following NEW packages will be installed:
  libqtcore4:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 2,061 kB of archives.
After this operation, 9,041 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ precise-updates/main libqtcore4 i386 4:4.8.1-0ubuntu4.1 [2,061 kB]
Fetched 2,061 kB in 3s (545 kB/s)       
(Reading database ... 181370 files and directories currently installed.)
Unpacking libqtcore4:i386 (from .../libqtcore4_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqtcore4_4%3a4.8.1-0ubuntu4.1_i386.deb (--unpack):
 conffile './etc/xdg/Trolltech.conf' is not in sync with other instances of the same package
Errors were encountered while processing:
 /var/cache/apt/archives/libqtcore4_4%3a4.8.1-0ubuntu4.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by matt_symes on 2012-05-14
Hi

It looks like this is a known bug.


[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/983315](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/983315)


Take a look at post #3 and #4 for an answer.


Kind regards

---

### Post by duodecillian on 2012-05-14
I don't mean to be a bother, but I'm having trouble understanding what to do with this information:

> Seems like a new version of the qt4 libs has been published today. Now libqtcore4 (and also Skype) installation is working for me again.

> I can confirm, after just downloading and installing the latest batch of patches there are no more dependency issues and Skype works fine.


Where exactly can I find these patches?

---

### Post by matt_symes on 2012-05-14
Hi

Don't worry. You're not a bother :)


This was the version they were using.


```
libqtcore4_4%3a4.8.1-0ubuntu4_i386.deb
```This is the version your are pulling down from precise updates repo


```
libqtcore4_4%3a4.8.1-0ubuntu4_**1**_i386.deb
```According to this...


[http://www.ubuntuupdates.org/package/core/precise/main/updates/libqtcore4](http://www.ubuntuupdates.org/package/core/precise/main/updates/libqtcore4)


...a version was moved there on the second of May.


Try downloading the package libqtcore4_4%3a4.8.1-0ubuntu4_**1**_i386.deb from the llink above. You want the 32 bit version.


Download it to you home directory using a web browser then open a terminal and type


```
sudo dpkg -i *.deb
```If it installs then all well and good (i am not convinced it will work though). Try 


```
sudo apt-get -f install
```Post back any errors.


It may just be a case that you are downloading an older version of the package somehow.


Kind regards

---

### Post by duodecillian on 2012-05-15
Thank you so much! After much pain trying to find the solution on my own I wish I could have found something is straightforward as this. I tried to change the little prefix to solved, but I just edited it in the title. Only change I made to your instructions was that I installed the 64bit one, since I'm running a 64bit computer.

---

### Post by matt_symes on 2012-05-15
Hi

I'm glad it's fixed :D

Just a note to let you know you can mark a thread as solved using the thread tools drop down menu at the top right of the page level with the new reply button.

Kind regards

---

### Post by strid3r on 2012-07-06
THANKS matt_symes!

This worked, except I downloaded the 64 bit. 

I just ran:
```
sudo dpkg -i libqtcore4_4.8.1-0ubuntu4.1_amd64.deb 
```

and then:
```
sudo apt-get -f install 
```


Worked like a charm!

---

