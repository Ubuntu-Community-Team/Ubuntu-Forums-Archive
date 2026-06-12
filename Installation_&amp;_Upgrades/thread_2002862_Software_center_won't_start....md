---
title: "Software center won't start..."
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by nipunshakya on 2012-06-13
Hello gurus. I tried to run 
```

winuxuser@magicbox:~$ sudo apt-get update
[sudo] password for winuxuser: 
Ign http://np.archive.ubuntu.com precise InRelease                             
Ign http://np.archive.ubuntu.com precise-updates InRelease                     
Ign http://np.archive.ubuntu.com precise-backports InRelease             
Ign http://np.archive.ubuntu.com precise-security InRelease              
Ign http://archive.canonical.com precise InRelease                       
Get:1 http://np.archive.ubuntu.com precise Release.gpg [198 B]           
Get:2 http://np.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:3 http://np.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Get:4 http://np.archive.ubuntu.com precise-security Release.gpg [198 B]        
Hit http://np.archive.ubuntu.com precise Release                               
Hit http://np.archive.ubuntu.com precise-updates Release                       
Hit http://np.archive.ubuntu.com precise-backports Release                     
Ign http://np.archive.ubuntu.com precise Release                               
Ign http://np.archive.ubuntu.com precise-updates Release                       
Ign http://np.archive.ubuntu.com precise-backports Release                     
Get:5 http://np.archive.ubuntu.com precise-security Release [49.6 kB]          
Get:6 http://archive.canonical.com precise Release.gpg [198 B]               
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://np.archive.ubuntu.com precise/main Sources/DiffIndex          
Ign http://np.archive.ubuntu.com precise/restricted Sources/DiffIndex
Ign http://np.archive.ubuntu.com precise/universe Sources/DiffIndex   
Ign http://np.archive.ubuntu.com precise/multiverse Sources/DiffIndex 
Ign http://np.archive.ubuntu.com precise/main amd64 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise/restricted amd64 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise/universe amd64 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise/multiverse amd64 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise/main i386 Packages/DiffIndex 
Ign http://np.archive.ubuntu.com precise/restricted i386 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise/universe i386 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise/multiverse i386 Packages/DiffIndex
Hit http://np.archive.ubuntu.com precise/main TranslationIndex        
Hit http://np.archive.ubuntu.com precise/multiverse TranslationIndex  
Hit http://np.archive.ubuntu.com precise/restricted TranslationIndex  
Hit http://archive.canonical.com precise Release                      
Ign http://archive.canonical.com precise Release                       
Hit http://np.archive.ubuntu.com precise/universe TranslationIndex     
Ign http://np.archive.ubuntu.com precise-updates/main Sources/DiffIndex
Ign http://np.archive.ubuntu.com precise-updates/restricted Sources/DiffIndex
Ign http://np.archive.ubuntu.com precise-updates/universe Sources/DiffIndex
Ign http://np.archive.ubuntu.com precise-updates/multiverse Sources/DiffIndex
Ign http://np.archive.ubuntu.com precise-updates/main amd64 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-updates/restricted amd64 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-updates/universe amd64 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-updates/multiverse amd64 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-updates/main i386 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-updates/restricted i386 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-updates/universe i386 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-updates/multiverse i386 Packages/DiffIndex
Hit http://np.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://np.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://np.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://np.archive.ubuntu.com precise-updates/universe TranslationIndex
Ign http://np.archive.ubuntu.com precise-backports/main Sources/DiffIndex
Ign http://np.archive.ubuntu.com precise-backports/restricted Sources/DiffIndex
Ign http://np.archive.ubuntu.com precise-backports/universe Sources/DiffIndex
Ign http://np.archive.ubuntu.com precise-backports/multiverse Sources/DiffIndex
Ign http://np.archive.ubuntu.com precise-backports/main amd64 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-backports/restricted amd64 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-backports/universe amd64 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-backports/multiverse amd64 Packages/DiffIndex
Get:7 http://extras.ubuntu.com precise Release.gpg [72 B]             
Ign http://np.archive.ubuntu.com precise-backports/main i386 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-backports/restricted i386 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-backports/universe i386 Packages/DiffIndex
Ign http://np.archive.ubuntu.com precise-backports/multiverse i386 Packages/DiffIndex
Hit http://np.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://np.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://np.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://np.archive.ubuntu.com precise-backports/universe TranslationIndex
Ign http://archive.canonical.com precise/partner Sources/DiffIndex    
Get:8 http://np.archive.ubuntu.com precise-security/main Sources [12.6 kB]
Get:9 http://np.archive.ubuntu.com precise-security/restricted Sources [14 B] 
Get:10 http://np.archive.ubuntu.com precise-security/universe Sources [4,522 B]
Get:11 http://np.archive.ubuntu.com precise-security/multiverse Sources [696 B]
Get:12 http://np.archive.ubuntu.com precise-security/main amd64 Packages [42.8 kB]
Hit http://extras.ubuntu.com precise Release                                   
Err http://extras.ubuntu.com precise Release                                   
  
Get:13 http://np.archive.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:14 http://np.archive.ubuntu.com precise-security/universe amd64 Packages [10.3 kB]
Ign http://archive.canonical.com precise/partner amd64 Packages/DiffIndex      
Ign http://archive.canonical.com precise/partner i386 Packages/DiffIndex
Ign http://archive.canonical.com precise/partner TranslationIndex
Get:15 http://np.archive.ubuntu.com precise-security/multiverse amd64 Packages [1,142 B]
Get:16 http://np.archive.ubuntu.com precise-security/main i386 Packages [43.9 kB]
Get:17 http://np.archive.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:18 http://np.archive.ubuntu.com precise-security/universe i386 Packages [10.3 kB]
Get:19 http://np.archive.ubuntu.com precise-security/multiverse i386 Packages [1,393 B]
Get:20 http://np.archive.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:21 http://np.archive.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:22 http://np.archive.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:23 http://np.archive.ubuntu.com precise-security/universe TranslationIndex [72 B]
Hit http://np.archive.ubuntu.com precise/main Sources
Hit http://np.archive.ubuntu.com precise/restricted Sources
Hit http://archive.canonical.com precise/partner Sources
Hit http://np.archive.ubuntu.com precise/universe Sources
Hit http://np.archive.ubuntu.com precise/multiverse Sources
Hit http://np.archive.ubuntu.com precise/main amd64 Packages
Hit http://np.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://np.archive.ubuntu.com precise/universe amd64 Packages
Hit http://np.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://np.archive.ubuntu.com precise/main i386 Packages
Hit http://np.archive.ubuntu.com precise/restricted i386 Packages
Hit http://np.archive.ubuntu.com precise/universe i386 Packages
Hit http://np.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://np.archive.ubuntu.com precise/main Translation-en
Hit http://np.archive.ubuntu.com precise/multiverse Translation-en
Hit http://np.archive.ubuntu.com precise/restricted Translation-en
Hit http://np.archive.ubuntu.com precise/universe Translation-en
Hit http://np.archive.ubuntu.com precise-updates/main Sources
Hit http://np.archive.ubuntu.com precise-updates/restricted Sources
Hit http://np.archive.ubuntu.com precise-updates/universe Sources
Hit http://np.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://np.archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://np.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://np.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://np.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://np.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://np.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://np.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://np.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://np.archive.ubuntu.com precise-updates/main Translation-en
Hit http://np.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://np.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://np.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://np.archive.ubuntu.com precise-backports/main Sources
Hit http://np.archive.ubuntu.com precise-backports/restricted Sources
Hit http://archive.canonical.com precise/partner amd64 Packages
Hit http://archive.canonical.com precise/partner i386 Packages
Hit http://np.archive.ubuntu.com precise-backports/universe Sources
Hit http://np.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://np.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://np.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://np.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://np.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://np.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://np.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://np.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://np.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://np.archive.ubuntu.com precise-backports/main Translation-en
Hit http://np.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://np.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://np.archive.ubuntu.com precise-backports/universe Translation-en
Get:24 http://np.archive.ubuntu.com precise-security/main Translation-en [27.1 kB]
Get:25 http://np.archive.ubuntu.com precise-security/multiverse Translation-en [587 B]
Get:26 http://np.archive.ubuntu.com precise-security/restricted Translation-en [14 B]
Get:27 http://np.archive.ubuntu.com precise-security/universe Translation-en [8,835 B]
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Fetched 215 kB in 7s (26.9 kB/s)                                               
Reading package lists... Error!
W: GPG error: http://np.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://np.archive.ubuntu.com precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://np.archive.ubuntu.com precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.canonical.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
winuxuser@magicbox:~$ 

```
i looked at the file where error was generated... all i did was try to run an update from a wireless network connection while i was at college. Now when i try to run an update, i get that error... Im trying to update via an ethernet cable if that will make a difference...

Any suggestions guys and gurus?

Regards,WinuxUser

---

### Post by nipunshakya on 2012-06-13
Guys, please help...without update, my ubuntu is dying....:(

---

### Post by fantab on 2012-06-14
First of all run:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update

```Post the output of _apt-get update_ if there are any errors or warnings.

---

### Post by nipunshakya on 2012-06-14
Hello fantab... i tried the suggestions from the following link... and the errors i have received are at my last post on the link given below:
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/194077](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/194077)


Regards,WinuxUser

---

### Post by fantab on 2012-06-14
Looks like your apt cache ran out of space.

You can 

```
sudo apt-get autoclean
sudo apt-get clean
```If you have **Ubuntu-tweak tool** already installed then you can use_ computer-janitor_ to clean up your system/cache. 

The following command will tell you how much cache is being used or its current size..

```
du -sh /var/cache/apt/archives
```Try increasing the cache size by adding following line to /etc/apt/apt.conf.d/70debconf

**APT::Cache-Limit "100000000"**

save the file and update.

---

### Post by nipunshakya on 2012-06-14
> **fantab said:**
> Looks like your apt cache ran out of space.
The output suggests the same thing.... my cache was only 184 kb free on the current session...
**```
APT::Cache-Limit "100000000"
```**adding at the end of the file  /etc/apt/apt.conf.d/70debconf would only give an error as follows:
```
winuxuser@magicbox:~$ sudo vim /etc/apt/apt.conf.d/70debconf
[sudo] password for winuxuser: 
winuxuser@magicbox:~$ du -sh /var/cache/apt/archives
184K    /var/cache/apt/archives
winuxuser@magicbox:~$ sudo apt-get update
E: Syntax error /etc/apt/apt.conf.d/70debconf:5: Extra junk at end of file
winuxuser@magicbox:~$ 

 
```

---

### Post by fantab on 2012-06-14
If that is the only error (Syntax Error) you are getting then I hope you have removed that line and tried again. 

You should look for a way to increase your apt cache size. I wish I could help you more. I hope someone with proper solution takes a look here. 

Gook Luck...

---

### Post by nipunshakya on 2012-06-15
Hello fantab... i clearly know its a syntax error(i can understand that :) )
But after a long search, i made a clean restoration of packages without updating the cache...either way works fine for me..

---

