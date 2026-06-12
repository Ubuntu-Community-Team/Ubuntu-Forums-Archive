---
title: "&quot;apt-get install&quot; doesn't work on 12.04"
date: 2013-06-12
forum: Installation &amp; Upgrades
---

### Post by smss on 2013-06-12
When I want to install kdevelop through Ubuntu Sofware Center, I faced with this error : "Package dependencies cannot be resolved".
I updated the resources and try it again, But the error wasn't changed.
```
smss@smss-network:~$ sudo apt-get update
Hit http://archive.canonical.com precise Release.gpg                       
Hit http://archive.canonical.com precise Release                           
Hit http://archive.ubuntu.com precise Release.gpg
Get:1 http://archive.ubuntu.com precise-security Release.gpg [198 B]
Hit http://archive.canonical.com precise/partner Sources  
Hit http://archive.ubuntu.com precise Release
Hit http://archive.canonical.com precise/partner amd64 Packages
Hit http://archive.canonical.com precise/partner i386 Packages
Ign http://archive.canonical.com precise/partner TranslationIndex
Get:2 http://archive.ubuntu.com precise-security Release [49.6 kB]
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://archive.canonical.com precise/partner Translation-en
Hit http://archive.ubuntu.com precise/main amd64 Packages                      
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                
Hit http://archive.ubuntu.com precise/universe amd64 Packages                  
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Get:3 http://archive.ubuntu.com precise-security/main amd64 Packages [286 kB]  
Get:4 http://archive.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:5 http://archive.ubuntu.com precise-security/universe amd64 Packages [75.2 kB]
Get:6 http://archive.ubuntu.com precise-security/multiverse amd64 Packages [2,182 B]
Get:7 http://archive.ubuntu.com precise-security/main i386 Packages [302 kB]   
Get:8 http://archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:9 http://archive.ubuntu.com precise-security/universe i386 Packages [77.9 kB]
Get:10 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2,367 B]
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-security/main Translation-en             
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en         
Fetched 805 kB in 1min 18s (10.3 kB/s)                                         
Reading package lists... Done
smss@smss-network:~$

```
I tried to install it through terminal, But I faced with these errors : 
```

smss@smss-network:~$ sudo apt-get install -f
[sudo] password for smss: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
smss@smss-network:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
smss@smss-network:~$ sudo apt-get install kdevelop-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kdevelop-dev : Depends: kdevelop (= 4:4.3.1-0ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
smss@smss-network:~$ 


```
Can anybody help me with this problem?
Thanks.

---

### Post by Petro Dawg on 2013-06-12
Have you tried...

```
[SIZE=2][FONT=arial]sudo apt-add-repository ppa:kubuntu-ppa/backports[/FONT][/SIZE]
```
[SIZE=3][FONT=arial]
[/FONT][/SIZE]```
[SIZE=2][FONT=arial]sudo apt-get install kdevelop[/FONT][/SIZE]
```

---

### Post by steeldriver on 2013-06-12
it looks like you pasted a lot of extraneous text into the command line e.g.

```

smss@smss-network:~$ [COLOR=#ff0000]**smss@smss-network:~$**[/COLOR] sudo apt-get install kdevelop-dev

```

and

```

smss@smss-network:~$ [COLOR=#ff0000]**Reading package lists... Done**[/COLOR]
Reading: command not found

```

etc.

---

### Post by smss on 2013-06-13
Excuse me stelldriver, I Updated it now.

Petro Dawg, For what I couldn't install programs through normally way?

---

### Post by Petro Dawg on 2013-06-13
> **smss said:**
> 
Petro Dawg, For what I couldn't install programs through normally way?

I do not understand your question.  

Were you able to install the program through terminal using the method I suggested?  If not, please copy and paste any new errors in the terminal output for further troubleshooting.

---

### Post by smss on 2013-06-13
In fact, I want to tell "apt-get" is not healthy in my PC... 
When I want to install any program such as "kdevelop" through terminal or other ways ( e.g. Ubuntu Software Center ), I could not install its and I faced with "E: Unable to correct problems, you have held broken packages."
```
smss@smss-network:~$ sudo add-apt-repository ppa:kubuntu-ppa/backports
[sudo] password for smss: 
You are about to add the following PPA to your system:
 Backports of new versions of KDE and major KDE apps for Kubuntu which are either too large a change or not yet tested enough to go to Ubuntu Backports.


 More info: https://launchpad.net/~kubuntu-ppa/+archive/backports
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpi4Yegj/secring.gpg' created
gpg: keyring `/tmp/tmpi4Yegj/pubring.gpg' created
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpi4Yegj/trustdb.gpg: trustdb created
gpg: key 8AC93F7A: public key "Launchpad Kubuntu Updates" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
smss@smss-network:~$ sudo apt-get update
Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://archive.ubuntu.com precise Release.gpg                              
Get:2 http://archive.ubuntu.com precise-security Release.gpg [198 B] 
Get:3 http://ppa.launchpad.net precise Release [11.9 kB]                       
Hit http://archive.ubuntu.com precise Release                                 
Get:4 http://ppa.launchpad.net precise/main Sources [75.9 kB]                  
Get:5 http://archive.ubuntu.com precise-security Release [49.6 kB]             
Hit http://archive.ubuntu.com precise/main amd64 Packages                      
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                
Hit http://archive.ubuntu.com precise/universe amd64 Packages                  
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Get:6 http://archive.ubuntu.com precise-security/main amd64 Packages [290 kB]  
Get:7 http://archive.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:8 http://archive.ubuntu.com precise-security/universe amd64 Packages [75.5 kB]
Get:9 http://ppa.launchpad.net precise/main amd64 Packages [144 kB]            
Get:10 http://archive.ubuntu.com precise-security/multiverse amd64 Packages [2,182 B]
Get:11 http://archive.ubuntu.com precise-security/main i386 Packages [306 kB]  
Get:12 http://ppa.launchpad.net precise/main i386 Packages [145 kB]            
Get:13 http://archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:14 http://archive.ubuntu.com precise-security/universe i386 Packages [78.2 kB]
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:15 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2,367 B]
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Ign http://ppa.launchpad.net precise/main Translation-en_US           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-security/main Translation-en             
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en         
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://archive.canonical.com precise Release
Hit http://archive.canonical.com precise/partner Sources
Hit http://archive.canonical.com precise/partner amd64 Packages
Hit http://archive.canonical.com precise/partner i386 Packages
Ign http://archive.canonical.com precise/partner TranslationIndex
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://archive.canonical.com precise/partner Translation-en
Fetched 1,190 kB in 2min 4s (9,579 B/s)
Reading package lists... Done
smss@smss-network:~$ sudo apt-get install kdevelop
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  kde-runtime kde-runtime-data kdevelop-custom-buildsystem kdevelop-data
  kdevplatform5-libs kubuntu-debug-installer libattica0.4 libkactivities-bin
  libkactivities-models1 libkactivities6 libkxmlrpcclient4 libnepomukcore4abi1
  libpoppler-qt4-3 libsoprano-dev libsoprano4 libsublime5 nepomuk-core
  nepomuk-core-data oxygen-icon-theme phonon plasma-scriptengine-javascript
  qapt-batch soprano-daemon
Suggested packages:
  djvulibre-bin finger cmake cvs konsole libsoprano-doc
  phonon-backend-gstreamer phonon-backend-vlc phonon-backend-xine
  phonon-backend-mplayer
The following NEW packages will be installed:
  kde-runtime kdevelop kdevelop-custom-buildsystem kdevelop-data
  kdevplatform5-libs kubuntu-debug-installer libattica0.4 libkactivities-bin
  libkactivities-models1 libkactivities6 libkxmlrpcclient4 libnepomukcore4abi1
  libpoppler-qt4-3 libsublime5 nepomuk-core nepomuk-core-data phonon
  qapt-batch
The following packages will be upgraded:
  kde-runtime-data libsoprano-dev libsoprano4 oxygen-icon-theme
  plasma-scriptengine-javascript soprano-daemon
6 upgraded, 18 newly installed, 0 to remove and 113 not upgraded.
Need to get 47.1 MB of archives.
After this operation, 53.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise-security/main libpoppler-qt4-3 amd64 0.18.4-1ubuntu3.1 [127 kB]
Get:2 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ precise/main libattica0.4 amd64 0.4.1-0ubuntu3~ubuntu12.04.1~ppa1 [281 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise/main phonon amd64 4:4.7.0really4.6.0-0ubuntu1 [7,414 B]                                                                                                       
Get:4 http://archive.ubuntu.com/ubuntu/ precise/universe kdevelop-data all 4:4.3.1-0ubuntu1 [3,450 kB]                                                                                                        
Get:5 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ precise/main kde-runtime-data all 4:4.10.4-0ubuntu0.1~ubuntu12.04~ppa1 [6,030 kB]                                                                
1% [4 kdevelop-data 27.8 kB/3,450 kB 1%] [5 kde-runtime-data 32.5 kB/6,030 kB 1%]                                                                                                          15.2 kB/s 50min 58s

```
With your given repository, I could install kdevelop, Thanks man

---

