---
title: "Bad samba package causing anoying errors over the whole system"
date: 2014-01-09
forum: Installation &amp; Upgrades
---

### Post by The musmula on 2014-01-09
last week it started and now it is even worse.
every time I try to install anything I get [this]("https://www.dropbox.com/s/39jkr04dlgvnz7s/error.png") error message:
[IMG]https://www.dropbox.com/s/39jkr04dlgvnz7s/error.png[/IMG]
sometimes I repeat the install, get the message once more and everything is fine (yeah right... everything is fine with the installed program, not with my system).

And this is one more desperate attempt to ask you people for help at a WAAAAAY bigger issue. I'll make it short:
my system is becoming a dumb piece of crap...

Here is the little bit longer short version without my rage:
[LIST]
[*][Empty windows]("https://dl-web.dropbox.com/get/Screenshot%20from%202013-11-19%2011%3A55%3A41.png?w=AAD73mzohm60O0QTRMmEPMsarUQiiVRDUcFLnSW6sFawwQ")
[*]Blank screen after going out of full screen
[*]in last two installations, my hdd was COMPLETLEY FORMATED (and it deffenetley was NOT suposed to do that....NO!)
[*]_**complete freeze after about an hour work**_
[/LIST]
&#8203;I thought that Ubuntu is suposed to work for years without shutdown, now I see... not on my pc. I just want to throw this hdd out of the windows and get a 2TB SSD (I know: NOT POSSIBLE FOR THE TIME BEING) Now I understand why Cannonical is so focused on stability for the 14.04 version of ubuntu (I cant wait for April 17th 2014)

---

### Post by TheFu on 2014-01-09
You seem to have entered "APT-hell."  That usually happens when any of the following occurs:
* installing non-repository software
* using non-approved PPAs
* having file corruption in the /var/apt area

Installing software from non-Ubuntu repos is the quickest way I know to get into "APT-hell."

As to the system freezes - that is probably a completely different issue, but we need to concentrate on 1 problem at a time here.

Please copy/paste **relevant **text and use the "code" tags to make things line up.  Let's start by running:
```
sudo apt-get update
sudo apt-get upgrade
```
in a terminal.

We don't need to see lots of lines that don't show issues. Just key lines with major changes or failures. Copy/paste here, please.

---

### Post by The musmula on 2014-01-11
thanks for the quick reply and sorry for me being so slow on replying, I have been busy a lot.

So for the first command the output is:
```

Hit http://hr.archive.ubuntu.com precise Release.gpgGet:1 http://hr.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:2 http://hr.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://hr.archive.ubuntu.com precise Release                               
Get:3 http://hr.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://dl.google.com stable Release.gpg                                    
Get:4 http://hr.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://dl.google.com stable Release.gpg                                    
Get:5 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://hr.archive.ubuntu.com precise/main Sources                          
Hit http://hr.archive.ubuntu.com precise/restricted Sources                    
Hit http://hr.archive.ubuntu.com precise/universe Sources                      
Hit http://hr.archive.ubuntu.com precise/multiverse Sources                    
Hit http://hr.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://hr.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://hr.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://hr.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://hr.archive.ubuntu.com precise/main i386 Packages                    
Hit http://archive.canonical.com precise Release                               
Hit http://dl.google.com stable Release                                        
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://hr.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://hr.archive.ubuntu.com precise/universe i386 Packages                
Hit http://hr.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://hr.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://hr.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://hr.archive.ubuntu.com precise/restricted TranslationIndex           
Get:7 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://dl.google.com stable Release                                        
Hit http://hr.archive.ubuntu.com precise/universe TranslationIndex             
Get:8 http://hr.archive.ubuntu.com precise-updates/main Sources [444 kB]       
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:9 http://ppa.launchpad.net precise Release [11.9 kB]                       
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://download.virtualbox.org precise Release.gpg                         
Hit http://archive.canonical.com precise/partner amd64 Packages                
Get:10 http://linux.dropbox.com precise Release.gpg [489 B]                    
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:11 http://security.ubuntu.com precise-security Release [49.6 kB]           
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://download.virtualbox.org precise Release                             
Ign http://dl.google.com stable/main TranslationIndex                          
Get:12 http://linux.dropbox.com precise Release [2,603 B]                      
Get:13 http://download.ebz.epson.net lsb3.2 Release.gpg [189 B]                
Get:14 http://ppa.launchpad.net precise/main Sources [4,022 B]                 
Get:15 http://ppa.launchpad.net precise/main amd64 Packages [4,242 B]          
Get:16 http://ppa.launchpad.net precise/main i386 Packages [4,228 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://download.virtualbox.org precise/contrib amd64 Packages              
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Get:17 http://linux.dropbox.com precise/main amd64 Packages [1,142 B]          
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://download.virtualbox.org precise/contrib i386 Packages               
Hit http://download.ebz.epson.net lsb3.2 Release                               
Ign http://download.ebz.epson.net lsb3.2 Release                               
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:18 http://security.ubuntu.com precise-security/main Sources [95.4 kB]      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Get:19 http://linux.dropbox.com precise/main i386 Packages [1,142 B]           
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Ign http://download.virtualbox.org precise/contrib TranslationIndex            
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Get:20 http://hr.archive.ubuntu.com precise-updates/restricted Sources [7,039 B]
Get:21 http://hr.archive.ubuntu.com precise-updates/universe Sources [101 kB]  
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://download.ebz.epson.net lsb3.2/main amd64 Packages/DiffIndex         
Ign http://archive.canonical.com precise/partner Translation-en_US             
Get:22 http://hr.archive.ubuntu.com precise-updates/multiverse Sources [8,468 B]
Get:23 http://hr.archive.ubuntu.com precise-updates/main amd64 Packages [740 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://download.ebz.epson.net lsb3.2/main i386 Packages/DiffIndex          
Ign http://download.ebz.epson.net lsb3.2/main TranslationIndex                 
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:24 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:25 http://security.ubuntu.com precise-security/universe Sources [29.9 kB]  
Ign http://dl.google.com stable/main Translation-en_US                         
Get:26 http://security.ubuntu.com precise-security/multiverse Sources [1,792 B]
Get:27 http://security.ubuntu.com precise-security/main amd64 Packages [354 kB]
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://download.virtualbox.org precise/contrib Translation-en_US           
Get:28 http://hr.archive.ubuntu.com precise-updates/restricted amd64 Packages [11.4 kB]
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Get:29 http://hr.archive.ubuntu.com precise-updates/universe amd64 Packages [228 kB]
Ign http://linux.dropbox.com precise/main Translation-en_US                    
Ign http://download.virtualbox.org precise/contrib Translation-en              
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:30 http://hr.archive.ubuntu.com precise-updates/multiverse amd64 Packages [14.2 kB]
Get:31 http://hr.archive.ubuntu.com precise-updates/main i386 Packages [764 kB]
Get:32 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:33 http://security.ubuntu.com precise-security/universe amd64 Packages [86.8 kB]
Get:34 http://hr.archive.ubuntu.com precise-updates/restricted i386 Packages [11.5 kB]
Get:35 http://hr.archive.ubuntu.com precise-updates/universe i386 Packages [233 kB]
Get:36 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,446 B]
Get:37 http://security.ubuntu.com precise-security/main i386 Packages [375 kB] 
Hit http://download.ebz.epson.net lsb3.2/main amd64 Packages                   
Get:38 http://hr.archive.ubuntu.com precise-updates/multiverse i386 Packages [14.4 kB]
Get:39 http://hr.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:40 http://hr.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:41 http://hr.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:42 http://hr.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:43 http://hr.archive.ubuntu.com precise-backports/main Sources [4,225 B]   
Get:44 http://hr.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:45 http://hr.archive.ubuntu.com precise-backports/universe Sources [36.4 kB]
Get:46 http://hr.archive.ubuntu.com precise-backports/multiverse Sources [5,311 B]
Get:47 http://hr.archive.ubuntu.com precise-backports/main amd64 Packages [4,800 B]
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages                    
Get:48 http://hr.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:49 http://hr.archive.ubuntu.com precise-backports/universe amd64 Packages [37.9 kB]
Get:50 http://hr.archive.ubuntu.com precise-backports/multiverse amd64 Packages [5,206 B]
Get:51 http://hr.archive.ubuntu.com precise-backports/main i386 Packages [4,809 B]
Get:52 http://hr.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:53 http://hr.archive.ubuntu.com precise-backports/universe i386 Packages [37.7 kB]
Get:54 http://hr.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,178 B]
Get:55 http://hr.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:56 http://hr.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:57 http://hr.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:58 http://hr.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Hit http://hr.archive.ubuntu.com precise/main Translation-en                   
Hit http://hr.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://hr.archive.ubuntu.com precise/restricted Translation-en             
Hit http://hr.archive.ubuntu.com precise/universe Translation-en               
Get:59 http://hr.archive.ubuntu.com precise-updates/main Translation-en [332 kB]
Ign http://download.ebz.epson.net lsb3.2/main Translation-en_US                
Hit http://hr.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://hr.archive.ubuntu.com precise-updates/restricted Translation-en     
Get:60 http://hr.archive.ubuntu.com precise-updates/universe Translation-en [134 kB]
Hit http://hr.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://hr.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://hr.archive.ubuntu.com precise-backports/restricted Translation-en   
Get:61 http://hr.archive.ubuntu.com precise-backports/universe Translation-en [27.7 kB]
Ign http://download.ebz.epson.net lsb3.2/main Translation-en                   
Get:62 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:63 http://security.ubuntu.com precise-security/universe i386 Packages [91.1 kB]
Get:64 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,642 B]
Get:65 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:66 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:67 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:68 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:69 http://security.ubuntu.com precise-security/main Translation-en [166 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Fetched 4,620 kB in 11s (418 kB/s)                                             
Reading package lists... Done
W: GPG error: http://download.ebz.epson.net lsb3.2 Release: The following signatures were invalid: BADSIG E5E86C008AA65D56 Seiko Epson Corporation (Epson Inkjet Printer Driver) <epson-linux-inkjet@avasys.jp>



```

The second commands output is:
```
E: Invalid operation uprade
```

:) yeah, I think you meant sudo apt-get **upgrade**, so for that the output is:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  base-files consolekit libck-connector0 libpam-ck-connector
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 200 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://hr.archive.ubuntu.com/ubuntu/ precise-updates/main base-files amd64 6.5ubuntu6.7 [61.0 kB]
Get:2 http://hr.archive.ubuntu.com/ubuntu/ precise-updates/main libck-connector0 amd64 0.4.5-2ubuntu0.1 [10.4 kB]
Get:3 http://hr.archive.ubuntu.com/ubuntu/ precise-updates/main consolekit amd64 0.4.5-2ubuntu0.1 [120 kB]
Get:4 http://hr.archive.ubuntu.com/ubuntu/ precise-updates/main libpam-ck-connector amd64 0.4.5-2ubuntu0.1 [8,188 B]
Fetched 200 kB in 0s (452 kB/s)                
(Reading database ... 386017 files and directories currently installed.)
Preparing to replace base-files 6.5ubuntu6.6 (using .../base-files_6.5ubuntu6.7_amd64.deb) ...
Unpacking replacement base-files ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
Setting up base-files (6.5ubuntu6.7) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Installing new version of config file /etc/os-release ...
Processing triggers for plymouth-theme-ubuntu-text ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-35-generic
(Reading database ... 386017 files and directories currently installed.)
Preparing to replace libck-connector0 0.4.5-2 (using .../libck-connector0_0.4.5-2ubuntu0.1_amd64.deb) ...
Unpacking replacement libck-connector0 ...
Preparing to replace consolekit 0.4.5-2 (using .../consolekit_0.4.5-2ubuntu0.1_amd64.deb) ...
Unpacking replacement consolekit ...
Preparing to replace libpam-ck-connector 0.4.5-2 (using .../libpam-ck-connector_0.4.5-2ubuntu0.1_amd64.deb) ...
Unpacking replacement libpam-ck-connector ...
Processing triggers for man-db ...
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
Setting up libck-connector0 (0.4.5-2ubuntu0.1) ...
Setting up consolekit (0.4.5-2ubuntu0.1) ...
Setting up libpam-ck-connector (0.4.5-2ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by TheFu on 2014-01-11
There is an external PPA that is broken. Looks like something related to a printer. Fix that or remove it.
If that doesn't make everything work again, force the samba4 package to be removed using apt-get. Do NOT just delete files.

---

### Post by The musmula on 2014-01-11
what external ppa? and how do I remove it?

How to FORCE samba to get removed? what can I do besides uninstalling it and deleting the files?

---

### Post by The musmula on 2014-01-13
Ok, I found a way to "Purge" programs, but still I cant install the software ](*,)

I cannot install ANYTHING anymore :shock:

---

### Post by TheFu on 2014-01-13
Please paste the relevant output from the command with the last errors. We don't need to see lists of URLS that worked. Just the failures.  If the first repo issue pointed out above AND shown in your initial post hasn't been fixed, correct that first by removing the problem repo from your /etc/apt/ sources*

When making changes like these, please always, always, always make a backup of any files you change so it is clear and can be put back later.

---

### Post by ibjsb4 on 2014-01-13
This does not have to be a PPA, could of been installed through the software center.

[ATTACH=CONFIG]249472[/ATTACH]

And if so can be removed by:

```
sudo apt-get remove --purge samba4
```

---

### Post by The musmula on 2014-01-13
I LOVE YOU... no homo
I have purged samba and installed a program via terminal, and it worked perfectly fine. It was not possible through the SC but I'm sure that this will be possible again as soon as I log out, and back in of course.
OH THAAAAAAAAAAAAAANK YOU!!!

---

### Post by ibjsb4 on 2014-01-13
About GPG Errors:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+BADSIG&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+BADSIG&sa=Search&cof=FORID:9)

And if this is fixed:

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

