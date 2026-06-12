---
title: "More trouble updating from 12.04 to 12.10"
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by cluelesswonder on 2013-08-14
Hello,

I was trying to upgrade my system to 12.10 last week and asked for help on the forum.
I thought the problem was solved and was going through the upgrade process and even almost finished but the internet connection was really slow and I kept having to quit with about 50 packages to download :(

Now when I try, I keep getting the same error message: 

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
[http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources) 
404 Not Found [IP: 91.189.91.13 80] 
, W:Failed to fetch 
[http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages) 
404 Not Found [IP: 91.189.91.13 80] 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 

I can send the whole attempted upgrade if necessary. Can anyone help me figure out what's wrong?

---

### Post by grahammechanical on 2013-08-14
You know what is wrong. Due to network issues the upgrade has not completed. You need to complete the upgrade. Can you still load Ubuntu? Have you tried running the upgrade again? Did you use the Update Manager? Try using the terminal. Sometimes with an error like this the terminal will give us advice on how to fix it.

I am sure that the download process will only download those packages that are not already downloaded. Once the full set of packages is downloaded the installation of them will begin. Do not lose power at this stage.

You could try

```
sudo apt-get update
```

That will indentify what packages are needed

```
sudo apt-get upgrade
```

that will download needed packages. It does not upgrade from one version of Ubuntu to another but only upgrade already installed packages with newer versions. It may download and install those missing 12.10 packages.

```
sudo do-release-upgrade
```

will run the upgrade to a new release.

Look for error messages in the terminal and any advice that is given.

Regards.

---

### Post by cluelesswonder on 2013-08-14
Thank you for your reply.
I originally tried to upgrade in update manager but the most recent error messages were copied from terminal.

After the error message it restores the system to its original state (which is also what happened both times I was trying to upgrade to 12.10 from update manager and cancelled before it could finish). . .
No problems in sudo apt-get update:
```
enigma@Peanut:~$ sudo apt-get update
[sudo] password for enigma: 
Hit http://ca.archive.ubuntu.com quantal Release.gpg
Hit http://security.ubuntu.com quantal-security Release.gpg                    
Hit http://extras.ubuntu.com quantal Release.gpg                               
Hit http://archive.canonical.com quantal Release.gpg                 
Hit http://security.ubuntu.com quantal-security Release              
Get:1 http://ca.archive.ubuntu.com quantal-updates Release.gpg [933 B]
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://archive.canonical.com quantal Release                               
Hit http://ca.archive.ubuntu.com quantal-backports Release.gpg                 
Hit http://security.ubuntu.com quantal-security/main Sources                   
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://archive.canonical.com quantal/partner i386 Packages       
Hit http://ca.archive.ubuntu.com quantal Release                     
Hit http://security.ubuntu.com quantal-security/restricted Sources             
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Ign http://archive.canonical.com quantal/partner TranslationIndex              
Hit http://security.ubuntu.com quantal-security/universe Sources     
Ign http://extras.ubuntu.com quantal/main TranslationIndex                     
Hit http://security.ubuntu.com quantal-security/multiverse Sources             
Hit http://security.ubuntu.com quantal-security/main i386 Packages             
Get:2 http://ca.archive.ubuntu.com quantal-updates Release [49.6 kB]           
Hit http://security.ubuntu.com quantal-security/restricted i386 Packages       
Hit http://ca.archive.ubuntu.com quantal-backports Release                     
Hit http://security.ubuntu.com quantal-security/universe i386 Packages         
Hit http://ca.archive.ubuntu.com quantal/main Sources                          
Hit http://security.ubuntu.com quantal-security/multiverse i386 Packages       
Hit http://ca.archive.ubuntu.com quantal/restricted Sources                    
Hit http://security.ubuntu.com quantal-security/main TranslationIndex 
Hit http://security.ubuntu.com quantal-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com quantal-security/restricted TranslationIndex    
Ign http://archive.canonical.com quantal/partner Translation-en_CA             
Hit http://security.ubuntu.com quantal-security/universe TranslationIndex      
Ign http://extras.ubuntu.com quantal/main Translation-en_CA                    
Ign http://archive.canonical.com quantal/partner Translation-en                
Hit http://security.ubuntu.com quantal-security/main Translation-en   
Ign http://extras.ubuntu.com quantal/main Translation-en              
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Hit http://security.ubuntu.com quantal-security/universe Translation-en
Get:3 http://ca.archive.ubuntu.com quantal/universe Sources [5,522 kB]         
Hit http://ca.archive.ubuntu.com quantal/multiverse Sources
Hit http://ca.archive.ubuntu.com quantal/main i386 Packages
Hit http://ca.archive.ubuntu.com quantal/restricted i386 Packages
Get:4 http://ca.archive.ubuntu.com quantal/universe i386 Packages [5,285 kB]   
Hit http://ca.archive.ubuntu.com quantal/multiverse i386 Packages              
Hit http://ca.archive.ubuntu.com quantal/main TranslationIndex                 
Hit http://ca.archive.ubuntu.com quantal/multiverse TranslationIndex           
Hit http://ca.archive.ubuntu.com quantal/restricted TranslationIndex           
Hit http://ca.archive.ubuntu.com quantal/universe TranslationIndex             
Get:5 http://ca.archive.ubuntu.com quantal-updates/main Sources [108 kB]       
Get:6 http://ca.archive.ubuntu.com quantal-updates/restricted Sources [2,564 B]
Get:7 http://ca.archive.ubuntu.com quantal-updates/universe Sources [90.8 kB]  
Get:8 http://ca.archive.ubuntu.com quantal-updates/multiverse Sources [3,985 B]
Get:9 http://ca.archive.ubuntu.com quantal-updates/main i386 Packages [276 kB] 
Get:10 http://ca.archive.ubuntu.com quantal-updates/restricted i386 Packages [4,841 B]
Get:11 http://ca.archive.ubuntu.com quantal-updates/universe i386 Packages [201 kB]
Get:12 http://ca.archive.ubuntu.com quantal-updates/multiverse i386 Packages [11.0 kB]
Hit http://ca.archive.ubuntu.com quantal-updates/main TranslationIndex         
Hit http://ca.archive.ubuntu.com quantal-updates/multiverse TranslationIndex   
Hit http://ca.archive.ubuntu.com quantal-updates/restricted TranslationIndex   
Hit http://ca.archive.ubuntu.com quantal-updates/universe TranslationIndex     
Hit http://ca.archive.ubuntu.com quantal-backports/main Sources                
Hit http://ca.archive.ubuntu.com quantal-backports/restricted Sources          
Hit http://ca.archive.ubuntu.com quantal-backports/universe Sources            
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse Sources          
Hit http://ca.archive.ubuntu.com quantal-backports/main i386 Packages          
Hit http://ca.archive.ubuntu.com quantal-backports/restricted i386 Packages    
Hit http://ca.archive.ubuntu.com quantal-backports/universe i386 Packages      
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse i386 Packages    
Hit http://ca.archive.ubuntu.com quantal-backports/main TranslationIndex       
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse TranslationIndex 
Hit http://ca.archive.ubuntu.com quantal-backports/restricted TranslationIndex 
Hit http://ca.archive.ubuntu.com quantal-backports/universe TranslationIndex   
Hit http://ca.archive.ubuntu.com quantal/main Translation-en_CA                
Hit http://ca.archive.ubuntu.com quantal/main Translation-en                   
Hit http://ca.archive.ubuntu.com quantal/multiverse Translation-en             
Hit http://ca.archive.ubuntu.com quantal/restricted Translation-en             
Hit http://ca.archive.ubuntu.com quantal/universe Translation-en_CA            
Hit http://ca.archive.ubuntu.com quantal/universe Translation-en               
Hit http://ca.archive.ubuntu.com quantal-updates/main Translation-en           
Hit http://ca.archive.ubuntu.com quantal-updates/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com quantal-updates/restricted Translation-en     
Hit http://ca.archive.ubuntu.com quantal-updates/universe Translation-en       
Hit http://ca.archive.ubuntu.com quantal-backports/main Translation-en         
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse Translation-en   
Hit http://ca.archive.ubuntu.com quantal-backports/restricted Translation-en   
Hit http://ca.archive.ubuntu.com quantal-backports/universe Translation-en     
Fetched 11.6 MB in 1min 21s (141 kB/s)                                         
Reading package lists... Done

```

sudo apt-get upgrade seems to be installing the packages that were stopped mid-install last time so this could be good. . .I'll update when it's finished.

---

### Post by cluelesswonder on 2013-08-14
These seem to be the only errors from sudo apt-get upgrade
```

INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
Segmentation fault
Processing triggers for install-info ...
Processing triggers for cups ...
Updating PPD files for foomatic-db-engine ...

Errors were encountered while processing:
 /var/cache/apt/archives/libsoup2.4-1_2.40.0-0ubuntu1_i386.deb
 /var/cache/apt/archives/libtelepathy-glib0_0.20.0-0ubuntu1_i386.deb
 /var/cache/apt/archives/libwxbase2.8-0_2.8.12.1-11ubuntu3.1_i386.deb
 /var/cache/apt/archives/libxvidcore4_2%3a1.3.2-9_i386.deb
 /var/cache/apt/archives/ppp_2.4.5-5ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by cluelesswonder on 2013-08-15
It seems that I have a problem with libsoup 2.4-1. I can't seem to install it.

sudo apt-get upgrade gives this result:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gir1.2-soup-2.4 : Depends: libsoup2.4-1 (>= 2.39.90) but 2.38.1-1 is installed
 libfolks-telepathy25 : Depends: libtelepathy-glib0 (>= 0.19.0) but 0.18.2-0ubuntu1 is installed
 libwebkitgtk-1.0-0 : Depends: libsoup2.4-1 (>= 2.39.3) but 2.38.1-1 is installed
 libwebkitgtk-3.0-0 : Depends: libsoup2.4-1 (>= 2.39.3) but 2.38.1-1 is installed
 telepathy-gabble : Depends: libtelepathy-glib0 (>= 0.19.1) but 0.18.2-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.
```

And in Synaptic I get this error message:
```

Preparing to replace libsoup2.4-1:i386 2.38.1-1 (using .../libsoup2.4-1_2.40.0-0ubuntu1_i386.deb) ...
Unpacking replacement libsoup2.4-1:i386 ...
dpkg-deb (subprocess): decompressing archive member: internal gzip read error: '<fd:4>: incorrect data check'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libsoup2.4-1_2.40.0-0ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Preparing to replace libtelepathy-glib0 0.18.2-0ubuntu1 (using .../libtelepathy-glib0_0.20.0-0ubuntu1_i386.deb) ...
Unpacking replacement libtelepathy-glib0:i386 ...
dpkg-deb (subprocess): decompressing archive member: internal gzip read error: '<fd:4>: incorrect data check'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libtelepathy-glib0_0.20.0-0ubuntu1_i386.deb (--unpack):
 cannot copy extracted data for './usr/lib/i386-linux-gnu/libtelepathy-glib.so.0.78.0' to '/usr/lib/i386-linux-gnu/libtelepathy-glib.so.0.78.0.dpkg-new': unexpected end of file or stream
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libsoup2.4-1_2.40.0-0ubuntu1_i386.deb
 /var/cache/apt/archives/libtelepathy-glib0_0.20.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libwebkitgtk-1.0-0:
 libwebkitgtk-1.0-0 depends on libsoup2.4-1 (>= 2.39.3); however:
  Version of libsoup2.4-1:i386 on system is 2.38.1-1.

dpkg: error processing libwebkitgtk-1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-soup-2.4:
 gir1.2-soup-2.4 depends on libsoup2.4-1 (>= 2.39.90); however:
  Version of libsoup2.4-1:i386 on system is 2.38.1-1.

dpkg: error processing gir1.2-soup-2.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of telepathy-gabble:
 telepathy-gabble depends on libtelepathy-glib0 (>= 0.19.1); however:
  Version of libtelepathy-glib0 on system is 0.18.2-0ubuntu1.

dpkg: error processing telepathy-gabble (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwebkitgtk-3.0-0:
 libwebkitgtk-3.0-0 depends on libsoup2.4-1 (>= 2.39.3); however:
  Version of libsoup2.4-1:i386 on system is 2.38.1-1.

dpkg: error processing libwebkitgtk-3.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-webkit-3.0:
 gir1.2-webkit-3.0 depends on gir1.2-soup-2.4; however:
  Package gir1.2-soup-2.4 is not configured yet.
 gir1.2-webkit-3.0 depends on libwebkitgtk-3.0-0 (>= 1.9.90); however:
  Package libwebkitgtk-3.0-0 is not configured yet.

dpkg: error processing gir1.2-webkit-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfolks-telepathy25:
 libfolks-telepathy25 depends on libtelepathy-glib0 (>= 0.19.0); however:
  Version of libtelepathy-glib0 on system is 0.18.2-0ubuntu1.

dpkg: error processing libfolks-telepathy25 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libyelp0:
 libyelp0 depends on libwebkitgtk-3.0-0 (>= 1.3.10); however:
  Package libwebkitgtk-3.0-0 is not configured yet.

dpkg: error processing libyelp0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on libwebkitgtk-3.0-0 (>= 1.3.10); however:
  Package libwebkitgtk-3.0-0 is not configured yet.
 yelp depends on libyelp0 (= 3.6.0-0ubuntu1); however:
  Package libyelp0 is not configured yet.

dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-webkit:
 python-webkit depends on libwebkitgtk-1.0-0 (>= 1.3.10); however:
  Package libwebkitgtk-1.0-0 is not configured yet.

dpkg: error processing python-webkit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libubuntuoneui-3.0-1:
 libubuntuoneui-3.0-1 depends on libwebkitgtk-3.0-0 (>= 1.3.10); however:
  Package libwebkitgtk-3.0-0 is not configured yet.

dpkg: error processing libubuntuoneui-3.0-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on yelp (>= 3); however:
  Package yelp is not configured yet.

dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-ubuntuoneui-3.0:
 gir1.2-ubuntuoneui-3.0 depends on libubuntuoneui-3.0-1 (>= 2.99.3); however:
  Package libubuntuoneui-3.0-1 is not configured yet.

dpkg: error processing gir1.2-ubuntuoneui-3.0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libwebkitgtk-1.0-0
 gir1.2-soup-2.4
 telepathy-gabble
 libwebkitgtk-3.0-0
 gir1.2-webkit-3.0
 libfolks-telepathy25
 libyelp0
 yelp
 python-webkit
 libubuntuoneui-3.0-1
 gnome-user-guide
 gir1.2-ubuntuoneui-3.0
```

Maybe I should be posting this in another section at this point?. . .but can anyone advise?

---

### Post by bapoumba on 2013-08-15
Please try running **sudo apt-get -f install** (first error message) and post the output, thanks.

---

### Post by cluelesswonder on 2013-08-16
The output for sudo apt-get -f install:

```
enigma@Peanut:~$ sudo apt-get -f install
[sudo] password for enigma: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsoup2.4-1 libtelepathy-glib0
The following packages will be upgraded:
  libsoup2.4-1 libtelepathy-glib0
2 upgraded, 0 newly installed, 0 to remove and 426 not upgraded.
12 not fully installed or removed.
Need to get 0 B/1,015 kB of archives.
After this operation, 332 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 674338 files and directories currently installed.)
Preparing to replace libsoup2.4-1:i386 2.38.1-1 (using .../libsoup2.4-1_2.40.0-0ubuntu1_i386.deb) ...
Unpacking replacement libsoup2.4-1:i386 ...
dpkg-deb (subprocess): decompressing archive member: internal gzip read error: '<fd:4>: incorrect data check'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libsoup2.4-1_2.40.0-0ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Preparing to replace libtelepathy-glib0 0.18.2-0ubuntu1 (using .../libtelepathy-glib0_0.20.0-0ubuntu1_i386.deb) ...
Unpacking replacement libtelepathy-glib0:i386 ...
dpkg-deb (subprocess): decompressing archive member: internal gzip read error: '<fd:4>: incorrect data check'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libtelepathy-glib0_0.20.0-0ubuntu1_i386.deb (--unpack):
 cannot copy extracted data for './usr/lib/i386-linux-gnu/libtelepathy-glib.so.0.78.0' to '/usr/lib/i386-linux-gnu/libtelepathy-glib.so.0.78.0.dpkg-new': unexpected end of file or stream
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libsoup2.4-1_2.40.0-0ubuntu1_i386.deb
 /var/cache/apt/archives/libtelepathy-glib0_0.20.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by cluelesswonder on 2013-08-19
no one. . .? :sad:

---

### Post by bapoumba on 2013-08-19
Have you been trying to install i386 libs on a 63-bit system ?
Both libs seem at their correct version number for quantal : 
[http://packages.ubuntu.com/quantal/libsoup2.4-1](http://packages.ubuntu.com/quantal/libsoup2.4-1)
[http://packages.ubuntu.com/search?keywords=libtelepathy-glib&searchon=names&suite=quantal&section=all](http://packages.ubuntu.com/search?keywords=libtelepathy-glib&searchon=names&suite=quantal&section=all)

Please try:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Lim_Xiang_Yann on 2013-08-19
> **bapoumba said:**
> Have you been trying to install i386 libs on a 63-bit system ?
Both libs seem at their correct version number for quantal : 
[http://packages.ubuntu.com/quantal/libsoup2.4-1](http://packages.ubuntu.com/quantal/libsoup2.4-1)
[http://packages.ubuntu.com/search?keywords=libtelepathy-glib&searchon=names&suite=quantal&section=all](http://packages.ubuntu.com/search?keywords=libtelepathy-glib&searchon=names&suite=quantal&section=all)

Please try:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```

Do you mean 64-bit (x64)?

Try replace the sources.list to the quantal version.

---

### Post by cluelesswonder on 2013-08-19
Thank you for your replies! 
Before reading them my computer froze and I rebooted. I went into the BIOS and tried to do a dpkg repair. . .which seemed to fix the errors with libsoup but then it got a bit hairy.
Said something about the screen. graphics card, input device being disabled. . .and I had to reboot and clean and run the dpkg repair again a couple of times but finally I am back! With 12.10 no less :)
I hope that was the last of my troubles before trying to upgrade to the next version!

Thank you so much :)

---

### Post by Lim_Xiang_Yann on 2013-08-19
Never tried like that =A=
But I'm happy that your problem is (maybe) solved
remember to mark the thread as solved.

---

### Post by bapoumba on 2013-08-19
> **Lim_Xiang_Yann said:**
> Do you mean 64-bit (x64)?


Yes sorry, not sure what kind of freudian slip this is :D

---

