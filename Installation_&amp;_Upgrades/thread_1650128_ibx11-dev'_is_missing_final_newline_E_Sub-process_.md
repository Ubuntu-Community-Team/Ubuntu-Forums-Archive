---
title: "ibx11-dev' is missing final newline E: Sub-process /usr/bin/dpkg returned an error co"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by shadow00 on 2010-12-21
[SIZE=3][I]Hello
 How are you?
 I hope that everyone is okay
 plz Can any one help me with this???:(

when i try to install anything i get at the end erorr [ 'libx11-dev' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2 ]

Selecting previously deselected package arj.
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libx11-dev' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2

[/I][/SIZE][SIZE=3][I]can anyone tell me what must i suppost to do?
[/I][/SIZE]

---

### Post by sikander3786 on 2010-12-21
Welcome to the forums :-)

From Applications > Accessories > Terminal, try these command and post the _complete_ output here.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get update && sudo apt-get upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

Thanks.

---

### Post by shadow00 on 2010-12-22
> **sikander3786 said:**
> Welcome to the forums :-)

From Applications > Accessories > Terminal, try these command and post the _complete_ output here.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
``````
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
``````
sudo apt-get update && sudo apt-get upgrade
```While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

Thanks.

Hello
i did what you told me to do 

```
kato@kato-G31M-ES2L:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
[sudo] password for kato: 
kato@kato-G31M-ES2L:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
kato@kato-G31M-ES2L:~$ sudo apt-get update && sudo apt-get upgrade
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/ailurus/ppa/ubuntu/ maverick/main Translation-en  
Ign http://ppa.launchpad.net/ailurus/ppa/ubuntu/ maverick/main Translation-en_US
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Get:2 http://extras.ubuntu.com maverick Release.gpg [65B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Get:3 http://security.ubuntu.com maverick-security Release [27.2kB]            
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Get:4 http://security.ubuntu.com maverick-security/main Sources [16.9kB]       
Get:5 http://security.ubuntu.com maverick-security/restricted Sources [14B]    
Get:6 http://security.ubuntu.com maverick-security/universe Sources [6,295B]   
Get:7 http://archive.getdeb.net maverick-getdeb Release.gpg [836B]             
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/games Translation-en     
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/games Translation-en_US  
Get:8 http://security.ubuntu.com maverick-security/multiverse Sources [649B]   
Get:9 http://security.ubuntu.com maverick-security/main i386 Packages [54.2kB] 
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Get:10 http://eg.archive.ubuntu.com maverick Release.gpg [198B]                
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US      
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en   
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US  
Get:11 http://eg.archive.ubuntu.com maverick-updates Release.gpg [198B]       
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en 
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://eg.archive.ubuntu.com maverick Release                             
Get:12 http://eg.archive.ubuntu.com maverick-updates Release [31.4kB]          
Hit http://eg.archive.ubuntu.com maverick/main Sources                         
Hit http://eg.archive.ubuntu.com maverick/restricted Sources                  
Hit http://eg.archive.ubuntu.com maverick/universe Sources                    
Get:13 http://archive.getdeb.net maverick-getdeb Release [7,246B]             
Hit http://eg.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://eg.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://eg.archive.ubuntu.com maverick/restricted i386 Packages             
Hit http://eg.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://eg.archive.ubuntu.com maverick/multiverse i386 Packages             
Get:14 http://eg.archive.ubuntu.com maverick-updates/main Sources [67.9kB]     
Get:15 http://eg.archive.ubuntu.com maverick-updates/restricted Sources [14B]  
Get:16 http://eg.archive.ubuntu.com maverick-updates/universe Sources [21.4kB] 
Get:17 http://eg.archive.ubuntu.com maverick-updates/multiverse Sources [1,068B]
Get:18 http://eg.archive.ubuntu.com maverick-updates/main i386 Packages [187kB]
Get:19 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:20 http://security.ubuntu.com maverick-security/universe i386 Packages [22.6kB]
Get:21 http://security.ubuntu.com maverick-security/multiverse i386 Packages [1,655B]
Hit http://archive.getdeb.net maverick-getdeb/games i386 Packages              
Get:22 http://eg.archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Get:23 http://eg.archive.ubuntu.com maverick-updates/universe i386 Packages [69.3kB]
Get:24 http://eg.archive.ubuntu.com maverick-updates/multiverse i386 Packages [2,522B]
Fetched 519kB in 1min 5s (7,959B/s)                                            
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
kato@kato-G31M-ES2L:~$ sudo dpkg --configure -a
kato@kato-G31M-ES2L:~$ sudo apt-get update && sudo apt-get upgrade
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/ailurus/ppa/ubuntu/ maverick/main Translation-en  
Ign http://ppa.launchpad.net/ailurus/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Hit http://eg.archive.ubuntu.com maverick Release.gpg                          
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://eg.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://eg.archive.ubuntu.com maverick Release                              
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://eg.archive.ubuntu.com maverick-updates Release                      
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://eg.archive.ubuntu.com maverick/main Sources                         
Hit http://eg.archive.ubuntu.com maverick/restricted Sources                   
Hit http://eg.archive.ubuntu.com maverick/universe Sources                     
Hit http://eg.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://eg.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://eg.archive.ubuntu.com maverick/restricted i386 Packages             
Hit http://eg.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://eg.archive.ubuntu.com maverick/multiverse i386 Packages             
Hit http://eg.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://eg.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://eg.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://eg.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://eg.archive.ubuntu.com maverick-updates/main i386 Packages           
Hit http://eg.archive.ubuntu.com maverick-updates/restricted i386 Packages     
Hit http://eg.archive.ubuntu.com maverick-updates/universe i386 Packages       
Hit http://eg.archive.ubuntu.com maverick-updates/multiverse i386 Packages     
Hit http://archive.getdeb.net maverick-getdeb Release.gpg                      
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/games Translation-en
Ign http://archive.getdeb.net/ubuntu/ maverick-getdeb/games Translation-en_US
Hit http://archive.getdeb.net maverick-getdeb Release    
Hit http://archive.getdeb.net maverick-getdeb/games i386 Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  gbrainy language-pack-en language-pack-gnome-en libgudev-1.0-0 libudev0
  linux-libc-dev udev
7 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 668kB/3,461kB of archives.
After this operation, 7,483kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main libudev0 i386 162-2.2 [126kB]
Get:2 http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main udev i386 162-2.2 [428kB]
Get:3 http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main libgudev-1.0-0 i386 1:162-2.2 [114kB]
Fetched 668kB in 1min 39s (6,743B/s)                                           
(Reading database ... 
dpkg: warning: files list file for package `libx11-dev' missing, assuming package has no files currently installed.
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'cfortran' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
kato@kato-G31M-ES2L:~$ 

```

what next ???:cry:

---

### Post by sikander3786 on 2010-12-23
```
sudo apt-get clean
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Please keep on posting the outputs.

---

### Post by shadow00 on 2010-12-23
> **sikander3786 said:**
> ```
sudo apt-get clean
``````
sudo apt-get install -f
``````
sudo dpkg --configure -a
```Please keep on posting the outputs.

hello
i did that too and i get that
```
kato@kato-G31M-ES2L:~$ sudo apt-get clean
[sudo] password for kato: 
kato@kato-G31M-ES2L:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
kato@kato-G31M-ES2L:~$ sudo dpkg --configure -a
kato@kato-G31M-ES2L:~$ 

```

---

### Post by sikander3786 on 2010-12-23
That seems fixed. Try installing some packages and see if that still returns some errors.

```
sudo apt-get upgrade
```

---

### Post by shadow00 on 2010-12-23
> **sikander3786 said:**
> That seems fixed. Try installing some packages and see if that still returns some errors.

```
sudo apt-get upgrade
```


i get the same error at the end
plz help me

```
kato@kato-G31M-ES2L:~$ sudo apt-get upgrade
[sudo] password for kato: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  gbrainy language-pack-en language-pack-gnome-en libgudev-1.0-0 libudev0
  linux-libc-dev udev
7 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 3,461kB of archives.
After this operation, 7,483kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.getdeb.net/ubuntu/ maverick-getdeb/games gbrainy all 1.60-1~getdeb1 [1,428kB]
Get:2 http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main language-pack-en all 1:10.10+20101204 [219kB]
Get:3 http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main language-pack-gnome-en all 1:10.10+20101204 [341kB]
Get:4 http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main libudev0 i386 162-2.2 [126kB]
Get:5 http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main udev i386 162-2.2 [428kB]
Get:6 http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main libgudev-1.0-0 i386 1:162-2.2 [114kB]
Get:7 http://eg.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-libc-dev i386 2.6.35-1024.42 [804kB]
Fetched 3,461kB in 1min 51s (31.2kB/s)                                         
(Reading database ... 
dpkg: warning: files list file for package `libx11-dev' missing, assuming package has no files currently installed.
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'cfortran' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
kato@kato-G31M-ES2L:~$ 

```

---

