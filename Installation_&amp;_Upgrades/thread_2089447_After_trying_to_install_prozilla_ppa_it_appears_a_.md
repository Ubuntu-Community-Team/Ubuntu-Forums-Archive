---
title: "After trying to install prozilla ppa it appears a red sign to the system tray"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by spiritualbird on 2012-11-29
The red sign says:
An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount is > 0'. This usually means that your installed packages have unmet dependencies 

When it try: sudo apt-get update
it appears the following:
```
Get:33 http://bd.archive.ubuntu.com precise-updates/main Sources [193 kB]      
Get:34 http://security.ubuntu.com precise-security/universe i386 Packages [58.4 kB]
97% [34 Packages bzip2 0 B] [33 Sources 164 kB/193 kB 85%] [Connecting to secur
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:35 http://bd.archive.ubuntu.com precise-updates/main Sources [193 kB]      
Get:36 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,388 B]
Get:37 http://bd.archive.ubuntu.com precise-updates/main Sources [193 kB]      
Get:38 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:39 http://bd.archive.ubuntu.com precise-updates/restricted Sources [4,419 B]
100% [39 Sources bzip2 0 B] [Connecting to bd.archive.ubuntu.com (116.193.170.1
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:40 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:41 http://bd.archive.ubuntu.com precise-updates/universe Sources [65.4 kB] 
Get:42 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get:43 http://bd.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:44 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:45 http://bd.archive.ubuntu.com precise-updates/main amd64 Packages [434 kB]
Get:46 http://bd.archive.ubuntu.com precise-updates/main amd64 Packages [434 kB]
Get:47 http://bd.archive.ubuntu.com precise-updates/main amd64 Packages [434 kB]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Get:48 http://bd.archive.ubuntu.com precise-updates/main amd64 Packages [434 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Get:49 http://bd.archive.ubuntu.com precise-updates/main amd64 Packages [434 kB]
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:50 http://bd.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:51 http://security.ubuntu.com precise-security/universe Translation-en [35.2 kB]
Get:52 http://bd.archive.ubuntu.com precise-updates/universe amd64 Packages [159 kB]
Err http://security.ubuntu.com precise-security/multiverse Sources             
  404  Not Found [IP: 91.189.92.190 80]
Get:53 http://bd.archive.ubuntu.com precise-updates/universe amd64 Packages [159 kB]
Get:54 http://bd.archive.ubuntu.com precise-updates/universe amd64 Packages [159 kB]
Get:55 http://bd.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:56 http://bd.archive.ubuntu.com precise-updates/main i386 Packages [442 kB]
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:57 http://bd.archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:58 http://bd.archive.ubuntu.com precise-updates/universe i386 Packages [160 kB]
Ign http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:59 http://bd.archive.ubuntu.com precise-updates/universe i386 Packages [160 kB]
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:60 http://bd.archive.ubuntu.com precise-updates/universe i386 Packages [160 kB]
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:61 http://bd.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:62 http://bd.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,661 B]
Ign http://ppa.launchpad.net precise Release.gpg                               
Get:63 http://bd.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:64 http://bd.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:65 http://bd.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Ign http://ppa.launchpad.net precise Release.gpg                               
Get:66 http://bd.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:67 http://bd.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://ppa.launchpad.net precise Release                                   
Get:68 http://bd.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Ign http://ppa.launchpad.net precise Release                                   
Get:69 http://bd.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Hit http://ppa.launchpad.net precise Release                                   
Get:70 http://bd.archive.ubuntu.com precise-backports/universe Sources [18.7 kB]
Hit http://ppa.launchpad.net precise Release                                   
Get:71 http://bd.archive.ubuntu.com precise-backports/universe Sources [18.7 kB]
Hit http://ppa.launchpad.net precise Release                                   
Get:72 http://bd.archive.ubuntu.com precise-backports/universe Sources [18.7 kB]
Hit http://ppa.launchpad.net precise Release                                   
Get:73 http://bd.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Ign http://ppa.launchpad.net precise Release                                   
Get:74 http://bd.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Hit http://ppa.launchpad.net precise Release                                   
Get:75 http://bd.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Hit http://ppa.launchpad.net precise Release                                   
Get:76 http://bd.archive.ubuntu.com precise-backports/universe amd64 Packages [16.7 kB]
Ign http://ppa.launchpad.net precise Release                                   
Get:77 http://bd.archive.ubuntu.com precise-backports/universe amd64 Packages [16.7 kB]
Hit http://ppa.launchpad.net precise Release                                   
Get:78 http://bd.archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]
Hit http://ppa.launchpad.net precise/main Sources                              
Get:79 http://bd.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Get:80 http://bd.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Get:81 http://bd.archive.ubuntu.com precise-backports/universe i386 Packages [16.7 kB]
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:82 http://bd.archive.ubuntu.com precise-backports/universe i386 Packages [16.7 kB]
100% [82 Packages bzip2 0 B] [Connecting to bd.archive.ubuntu.com (116.193.170.
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:83 http://bd.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Get:84 http://bd.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:85 http://bd.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:86 http://bd.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Hit http://ppa.launchpad.net precise/main Sources                              
Get:87 http://bd.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://bd.archive.ubuntu.com precise/main Translation-en                   
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://bd.archive.ubuntu.com precise/multiverse Translation-en             
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://bd.archive.ubuntu.com precise/restricted Translation-en             
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://bd.archive.ubuntu.com precise/universe Translation-en               
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Get:88 http://bd.archive.ubuntu.com precise-updates/main Translation-en [214 kB]
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Get:89 http://bd.archive.ubuntu.com precise-updates/main Translation-en [214 kB]
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://bd.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://bd.archive.ubuntu.com precise-updates/restricted Translation-en     
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:90 http://bd.archive.ubuntu.com precise-updates/universe Translation-en [95.6 kB]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Get:91 http://bd.archive.ubuntu.com precise-updates/universe Translation-en [95.6 kB]
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:92 http://bd.archive.ubuntu.com precise-updates/universe Translation-en [95.6 kB]
Get:93 http://bd.archive.ubuntu.com precise-updates/universe Translation-en [95.6 kB]
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://bd.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://bd.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://bd.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Err http://ppa.launchpad.net precise/main Sources    
  404  Not Found
Err http://ppa.launchpad.net precise/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main Sources    
  404  Not Found
Err http://ppa.launchpad.net precise/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main Sources    
  404  Not Found
Err http://ppa.launchpad.net precise/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
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
Fetched 875 kB in 4min 55s (2,965 B/s)
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources  404  Not Found [IP: 91.189.92.190 80]

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/bd.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/bd.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://bd.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Index  No sections in Release file /var/lib/apt/lists/partial/bd.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index

W: Failed to fetch http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/raof/aubergine/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/raof/aubergine/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/raof/aubergine/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-release/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-release/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-release/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

sudo apt-get install -f shows the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 language-pack-kde-zh-hans-base libgomp1:i386
  firefox-locale-zh-hans libcroco3:i386 language-pack-kde-en kde-l10n-engb
  libgettextpo0:i386 language-pack-zh-hans-base kde-l10n-zhcn
  language-pack-zh-hans language-pack-kde-zh-hans language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  prozilla
The following NEW packages will be installed:
  prozilla
0 upgraded, 1 newly installed, 0 to remove and 559 not upgraded.
1 not fully installed or removed.
Need to get 0 B/137 kB of archives.
After this operation, 523 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 184278 files and directories currently installed.)
Unpacking prozilla (from .../prozilla_2.0.4~precisebuild1-0tahutek1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/prozilla_2.0.4~precisebuild1-0tahutek1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/locale/locale.alias', which is also in package locales 2.13+git20120306-3
Errors were encountered while processing:
 /var/cache/apt/archives/prozilla_2.0.4~precisebuild1-0tahutek1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please help me to remove from the pain. I cannot update my system without solving the problem.

---

### Post by zvacet on 2012-11-30
In Ubuntu software center > edit> software repositories> switch server to main.Thar can help.Also,check why you can not get PPA´s.Are you sure you don´t have PPA from previous Ubuntu version?And you can try

```
sudo dpkg --configure -a
```

---

