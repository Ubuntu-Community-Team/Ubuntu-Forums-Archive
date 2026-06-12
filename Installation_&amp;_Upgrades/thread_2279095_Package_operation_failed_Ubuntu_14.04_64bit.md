---
title: "Package operation failed Ubuntu 14.04 64bit"
date: 2015-05-20
forum: Installation &amp; Upgrades
---

### Post by 1313tx on 2015-05-20
Hi,
I am new to using Ubuntu.  Recently I had an Ubuntu that I can't install.  When I start the Ubuntu Software Center I get New Software Can't be Installed... I click the Repair button but the the error: Package operation failed. Details: installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/status' near line 13064 package 'qtdeclarative5-qtquick2-plugin:amd64': field name `2015-05-18' must be followed by colon
Error in function: 

Any assistance would be appreciated.  Thank you!

---

### Post by dino99 on 2015-05-21
better to install & use 'synaptic' to do update/upgrade & see the package changelog if you wish

---

### Post by Bucky Ball on 2015-05-21
Welcome.

@dino99: Synaptics is better, in my opinion, but OP is asking about an issue with the Software Centre and wants a fix for that. There is a good chance that if SCentre isn't working, Synpatics won't either, as they are both frontends for apt. 

@ the OP: Open a terminal and:

```
sudo apt-get update
```

Please post any and all errors. If there are none, then:

```
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Again, post any errors. Thanks.

---

### Post by v3.xx on 2015-05-21
I have had luck with replacing /dpkg/status with /dpkg/status-old, but lets see the above request first.

---

### Post by dino99 on 2015-05-21
> **Bucky Ball said:**
> Welcome.

@dino99: Synaptics is better, in my opinion, but OP is asking about an issue with the Software Centre and wants a fix for that. There is a good chance that if SCentre isn't working, Synpatics won't either, as they are both frontends for apt. 

@ the OP: Open a terminal and:

```
sudo apt-get update
```

Please post any and all errors. If there are none, then:

```
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Again, post any errors. Thanks.

software center is so buggy, and quite not maintained : it even not have libgtk2-perl as a dependency (which is highly recommended when the package upgrade request a user decision, but prefer freezing  ;)

about the OP   'qtdeclarative5-qtquick2-plugin:amd64' guess it been picked in the wild

---

### Post by 1313tx on 2015-05-21
Everyone,
Thank you for your suggestions.  I apologize for my slow reply as my real job is interfering with productive work.

dino99: I tried to install synaptic but it pooped-out too.  

Bucky Ball: I'll start with your suggestions since it seems like it is focusing on the basics.
What I have done:
```
-sudo apt-get update - no problem
-sudo apt-get upgrade rendered the following:
paul@AG:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 colord : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 cups : Depends: cups-core-drivers (>= 1.7.2-0ubuntu1.5)
 cups-filters-core-drivers : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 eog : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 gcc : Depends: gcc-4.8 (>= 4.8.2-5~) but it is not installed
 gnome-keyring : Depends: libcap2-bin but it is not installed
 gnomine : Depends: gnome-mines but it is not installed
 libcdr-0.0-0 : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 libcolord1 : Depends: liblcms2-2 (>= 2.5) but it is not installed
 libemail-valid-perl : Depends: libnet-domain-tld-perl but it is not installed
 libgs9 : Depends: liblcms2-2 (>= 2.5) but it is not installed
 libgxps2 : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 libpoppler44 : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 libraw9 : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 libreoffice-core : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 lintian : Depends: liburi-perl but it is not installed
 poppler-utils : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 python-commandnotfound : Depends: python-gdbm but it is not installed
 python-pil : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 unity-settings-daemon : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
E: Unmet dependencies. Try using -f.
```

May I add I have attempted: sudo apt-upgrade -f, but no dice

---

### Post by wildmanne39 on 2015-05-21
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Bucky Ball on 2015-05-22
In your first post, you say 'Recently I had a Ubuntu that I can't install.' I had no idea what you meant by that, but as it didn't seem to factor at first, I ignored.

Looking at your output, though, please explain. Were you doing an update/upgrade and stopped part way through? Your errors give the impression this is the case. You seem to have some of the newer things installed by they didn't drag their dependencies with them perhaps. Curious as to how they may have been prevented from doing so. :-K

We'll continue to dig ...

@dino99: These issues would occur regardless of using SCentre, Synpatic, a terminal or anything else as they are generated using the apt command, which all of the above do for an update, and missing dependencies. ;)

---

### Post by v3.xx on 2015-05-22
@Bucky
My thoughts are still on post #1.  Maybe a 'dpkg --clear -avail' followed with another update?

@OP
Are your PPAs in order?
```
ls /etc/apt/sources.list.d/*.list
```

For reference
[https://www.google.com/search?client=ubuntu&channel=fs&q=failed%3A+dpkg%3A+error%3A+parsing+file+%27%2Fvar%2Flib%2Fdpkg%2Fstatus%27&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=failed%3A+dpkg%3A+error%3A+parsing+file+%27%2Fvar%2Flib%2Fdpkg%2Fstatus%27&ie=utf-8&oe=utf-8)
```
man dpkg
```

---

### Post by 1313tx on 2015-05-22
[COLOR=#000000]Bucky,

I was trying to install an update to Ubuntu 14.04 and was not able to do so successfully. Consequently, when I go to the Software Center I get 'New software can't be installed, because there is a problem with the software currently installed window. Do you want to repair this problem now?'[/COLOR]

[COLOR=#000000]I click Repair, and then get Package operation failed. When I click Details, I receive:[/COLOR]
```
[COLOR=#000000]installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/status' near line 13064 package 'qtdeclarative5-qtquick2-plugin:amd64':[/COLOR]
[COLOR=#000000]field name `2015-05-18' must be followed by colon[/COLOR]
[COLOR=#000000]Error in function: [/COLOR]
```

[COLOR=#000000]And that's where I am at.[/COLOR]

---

### Post by oldos2er on 2015-05-22
See [http://ubuntuforums.org/showthread.php?t=1816855](http://ubuntuforums.org/showthread.php?t=1816855) for possible solutions.

---

### Post by 1313tx on 2015-05-22
Hi oldos2er,
I tried the suggestion you posted, no luck.  Here's the results

```
paul@AG:~$ sudo mv/var/lib/dpkg/status/var/lib/dpkg/status.broken
[sudo] password for paul: 
sudo: mv/var/lib/dpkg/status/var/lib/dpkg/status.broken: command not found
paul@AG:~$ sudo mv /var/lib/dpkg/status/var/lib/dpkg/status.broken
mv: missing destination file operand after ‘/var/lib/dpkg/status/var/lib/dpkg/status.broken’
Try 'mv --help' for more information.
paul@AG:~$ sudo mv /var/lib/dpkg/status-old/var/lib/dpkg/status
mv: missing destination file operand after ‘/var/lib/dpkg/status-old/var/lib/dpkg/status’
Try 'mv --help' for more information.
paul@AG:~$ sudo apt-get update
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://us.archive.ubuntu.com trusty-backports InRelease 
Hit http://us.archive.ubuntu.com trusty Release.gpg         
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Get:2 http://us.archive.ubuntu.com trusty-backports Release.gpg [933 B]        
Hit http://us.archive.ubuntu.com trusty Release                                
Get:3 http://us.archive.ubuntu.com trusty-updates Release [63.5 kB]            
Get:4 http://us.archive.ubuntu.com trusty-backports Release [63.5 kB]          
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages               
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages              
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:5 http://us.archive.ubuntu.com trusty-updates/main Sources [205 kB]        
Get:6 http://us.archive.ubuntu.com trusty-updates/restricted Sources [3,433 B] 
Get:7 http://us.archive.ubuntu.com trusty-updates/universe Sources [117 kB]    
Get:8 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,152 B] 
Get:9 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [524 kB] 
Get:10 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [11.8 kB]
Get:11 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [280 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.9 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [513 kB] 
Get:14 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [11.8 kB]
Get:15 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [281 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Get:17 http://us.archive.ubuntu.com trusty-backports/main Sources [5,851 B]    
Get:18 http://us.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:19 http://us.archive.ubuntu.com trusty-backports/universe Sources [25.9 kB]
Get:20 http://us.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:21 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [6,256 B]
Get:22 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:23 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [29.7 kB]
Get:24 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,245 B]
Get:25 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [6,285 B]
Get:26 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:27 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [29.7 kB]
Get:28 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,249 B]
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Ign http://security.ubuntu.com trusty-security InRelease                       
Get:29 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:30 http://security.ubuntu.com trusty-security Release [63.5 kB]
Get:31 http://security.ubuntu.com trusty-security/main Sources [81.4 kB]
Get:32 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]
Get:33 http://security.ubuntu.com trusty-security/universe Sources [25.2 kB]
Get:34 http://security.ubuntu.com trusty-security/multiverse Sources [2,333 B]
Get:35 http://security.ubuntu.com trusty-security/main amd64 Packages [272 kB]
Get:36 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Get:37 http://security.ubuntu.com trusty-security/universe amd64 Packages [104 kB]
Get:38 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,681 B]
Get:39 http://security.ubuntu.com trusty-security/main i386 Packages [260 kB]
Get:40 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Get:41 http://security.ubuntu.com trusty-security/universe i386 Packages [104 kB]
Get:42 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,840 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Fetched 3,154 kB in 36s (85.5 kB/s)                                            
Reading package lists... Done
paul@AG:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 colord : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 cups : Depends: cups-core-drivers (>= 1.7.2-0ubuntu1.5)
 cups-filters-core-drivers : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 eog : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 gcc : Depends: gcc-4.8 (>= 4.8.2-5~) but it is not installed
 gnome-keyring : Depends: libcap2-bin but it is not installed
 gnomine : Depends: gnome-mines but it is not installed
 libcdr-0.0-0 : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 libcolord1 : Depends: liblcms2-2 (>= 2.5) but it is not installed
 libemail-valid-perl : Depends: libnet-domain-tld-perl but it is not installed
 libgs9 : Depends: liblcms2-2 (>= 2.5) but it is not installed
 libgxps2 : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 libpoppler44 : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 libraw9 : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 libreoffice-core : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 lintian : Depends: liburi-perl but it is not installed
 poppler-utils : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 python-commandnotfound : Depends: python-gdbm but it is not installed
 python-pil : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
 unity-settings-daemon : Depends: liblcms2-2 (>= 2.2+git20110628) but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by oldos2er on 2015-05-22
There's an error in your mv command. Try ```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broken
``` Spaces are important.

---

### Post by 1313tx on 2015-05-23
oldos2er,
Thanks for the correction.  I now get this:
```
paul@AG:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broken
[sudo] password for paul: 
paul@AG:~$ mv /var/lib/dpkg/status-old /var/lib/dpkg/status.broken
mv: try to overwrite ‘/var/lib/dpkg/status.broken’, overriding mode 0644 (rw-r--r--)? y

```

---

### Post by oldos2er on 2015-05-23
You only need to run that mv command once. Now try ```
sudo apt-get update
``` If there are errors please post the full output.

---

### Post by 1313tx on 2015-05-23
oldos2er,
Here's what I got:
```
paul@AG:~$ sudo apt-get update
[sudo] password for paul: 
Ign http://extras.ubuntu.com trusty InRelease
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://us.archive.ubuntu.com trusty-backports InRelease      
Hit http://us.archive.ubuntu.com trusty Release.gpg              
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://us.archive.ubuntu.com trusty Release                  
Get:2 http://us.archive.ubuntu.com trusty-updates Release [63.5 kB]            
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:3 http://us.archive.ubuntu.com trusty-updates/main Sources [205 kB]        
Ign http://security.ubuntu.com trusty-security InRelease                       
Get:4 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Get:5 http://us.archive.ubuntu.com trusty-updates/restricted Sources [3,433 B] 
Get:6 http://us.archive.ubuntu.com trusty-updates/universe Sources [117 kB]    
Get:7 http://security.ubuntu.com trusty-security Release [63.5 kB]             
Get:8 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,152 B] 
Get:9 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [524 kB] 
Get:10 http://security.ubuntu.com trusty-security/main Sources [81.4 kB]       
Get:11 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [11.8 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [280 kB]
Get:13 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B] 
Get:14 http://security.ubuntu.com trusty-security/universe Sources [25.2 kB]   
Get:15 http://security.ubuntu.com trusty-security/multiverse Sources [2,333 B] 
Get:16 http://security.ubuntu.com trusty-security/main amd64 Packages [272 kB] 
Get:17 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.9 kB]
Get:18 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [513 kB] 
Get:19 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Get:20 http://security.ubuntu.com trusty-security/universe amd64 Packages [104 kB]
Get:21 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,681 B]
Get:22 http://security.ubuntu.com trusty-security/main i386 Packages [260 kB]  
Get:23 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [11.8 kB]
Get:24 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [281 kB]
Get:25 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Get:26 http://security.ubuntu.com trusty-security/universe i386 Packages [104 kB]
Get:27 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Get:28 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,840 B]
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 2,981 kB in 38s (77.9 kB/s)                                            
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.
paul@AG:~$ 

```

---

### Post by oldos2er on 2015-05-24
Try ```
sudo apt-get upgrade
``` now.

---

### Post by v3.xx on 2015-05-24
```
paul@AG:~$ mv /var/lib/dpkg/status-old /var/lib/dpkg/status.broken
```
You moved it to the wrong place.

---

### Post by 1313tx on 2015-05-24
v3.xx,
To put the file  in the correct location use the following code?
paul@AG:~$ mv /var/lib/dpkg/status-old /var/lib/dpkg/status.broken

---

### Post by v3.xx on 2015-05-24
The link provided in post #11.
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broken
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by 1313tx on 2015-05-25
v3.xx, dino99 and oldos2er:
Thanks!  I got it running.

I did the following commands, restarted, and verified everything working and updated.  I opened Software Center with no issues!

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.broken
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Bucky Ball on 2015-05-25
Excellent news. ;)

Please mark thread as solved to help others (see second link in my signature). Good luck.

---

### Post by 1313tx on 2015-05-25
Thanks to you too Bucky!

---

