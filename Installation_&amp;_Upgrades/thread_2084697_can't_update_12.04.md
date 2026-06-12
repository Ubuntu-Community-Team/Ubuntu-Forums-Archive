---
title: "can't update 12.04"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by chetkgp on 2012-11-16
I installed a fresh ubuntu 12.04 on my i5 machine.
However the update manager fails with the following error.

E:Unable to parse package file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index (1)

Any idea what should be done to get the updates to work ?

---

### Post by chetkgp on 2012-11-16
When I do a
sudo apt-get update

I get several messages of the form.

Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages [73 B]   
91% [70 Packages bzip2 0 B] [Waiting for headers]                68.0 kB/s 12sbzip2: (stdin) is not a bzip2 file.

Could this be the reason for the " E:Unable to parse package file  /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index  (1)" error?

How do I fix this ?

---

### Post by ibjsb4 on 2012-11-16
In terminal:
[FONT=monospace]
[/FONT]sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

---

### Post by chetkgp on 2012-11-16
i tried 
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update 	

but the same error :(

---

### Post by NikTh on 2012-11-16
Hi , 
can you give here the results of this command ? 
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```Click on **"New Reply"** and put the results inside [CODE] tags to be easier to read. [See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by chetkgp on 2012-11-16
Hi NikTh

This is the output of the find command

```

/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/
     2    
     3    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted
     5    
     6    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7    # newer versions of the distribution.
     8    deb http://archive.ubuntu.com/ubuntu precise main restricted
     9    deb-src http://archive.ubuntu.com/ubuntu precise main restricted
    10    
    11    ## Major bug fix updates produced after the final release of the
    12    ## distribution.
    13    deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
    14    deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    deb http://archive.ubuntu.com/ubuntu precise universe
    20    deb-src http://archive.ubuntu.com/ubuntu precise universe
    21    deb http://archive.ubuntu.com/ubuntu precise-updates universe
    22    deb-src http://archive.ubuntu.com/ubuntu precise-updates universe
    23    
    24    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25    ## team, and may not be under a free licence. Please satisfy yourself as to 
    26    ## your rights to use the software. Also, please note that software in 
    27    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    28    ## security team.
    29    deb http://archive.ubuntu.com/ubuntu precise multiverse
    30    deb-src http://archive.ubuntu.com/ubuntu precise multiverse
    31    deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
    32    deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse
    33    
    34    ## N.B. software from this repository may not have been tested as
    35    ## extensively as that contained in the main release, although it includes
    36    ## newer versions of some applications which may provide useful features.
    37    ## Also, please note that software in backports WILL NOT receive any review
    38    ## or updates from the Ubuntu security team.
    39    deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
    40    deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
    41    
    42    deb http://archive.ubuntu.com/ubuntu precise-security main restricted
    43    deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
    44    deb http://archive.ubuntu.com/ubuntu precise-security universe
    45    deb-src http://archive.ubuntu.com/ubuntu precise-security universe
    46    deb http://archive.ubuntu.com/ubuntu precise-security multiverse
    47    deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse
    48    
    49    ## Uncomment the following two lines to add software from Canonical's
    50    ## 'partner' repository.
    51    ## This software is not part of Ubuntu, but is offered by Canonical and the
    52    ## respective vendors as a service to Ubuntu users.
    53    # deb http://archive.canonical.com/ubuntu precise partner
    54    # deb-src http://archive.canonical.com/ubuntu precise partner
    55    
    56    ## This software is not part of Ubuntu, but is offered by third-party
    57    ## developers who want to ship their latest software.
    58    deb http://extras.ubuntu.com/ubuntu precise main
    59    deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by raja.genupula on 2012-11-16
open your terminal and type as ```


sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

one more helpful link : [http://askubuntu.com/questions/190221/difference-between-sudo-rm-rf-and-rm-vf](http://askubuntu.com/questions/190221/difference-between-sudo-rm-rf-and-rm-vf)

---

### Post by ibjsb4 on 2012-11-16
Are you building or modifying software packages from source code?

If not, uncheck source code and update.  That may clear the problem.

 [https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Hi raja

---

### Post by chetkgp on 2012-11-16
@ ibjsb4

I unchecked all the source code but that doesn't help.

@ Raja.genupula

I've tried removing the lists already, but the error
still persists.

---

### Post by ibjsb4 on 2012-11-16
Try changing server

[https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)

---

### Post by chetkgp on 2012-11-16
I have tried changing the server as well,
but that too does'nt work!

---

### Post by NikTh on 2012-11-16
Hi , 
your sources list file seems perfect , but I have a query here.. where is the server ? Usually when you install Ubuntu it asks you for the Country and add automatically the appropriate server in your sources.list file. 
eg: for US the sources.list is something like 
```
http://**us.**archive.ubuntu.com/ubuntu/ precise blahblahblah
```

You can try this if you want. 
```
gksudo gedit /etc/apt/sources.list
```and comment out these lines 
```
29    deb http://archive.ubuntu.com/ubuntu precise multiverse
30    deb-src http://archive.ubuntu.com/ubuntu precise multiverse
31    deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
32    deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse
```place this symbol **#** at the start. Save the file and try again 
```
sudo apt-get update ; sudo apt-get dist-upgrade
```and see if working. Maybe the problem is temporally. 

You can re-enable these sources , by Un-commenting the lines (remove the symbol #)

Thanks

---

### Post by chetkgp on 2012-11-17
NikTh,

My location is in india. 
/etc/apt/sourses.list was initially set to an indian location.
I get the same error with this setting as well.

commenting the lines in sourses.list doesnt work either.

---

### Post by NikTh on 2012-11-17
Hi , 
can you please post the output of 
```
sudo apt-get update
``` 
Thanks

---

### Post by chetkgp on 2012-11-19
Hi NikTh

I ran the update today morning. It seems
to show a new set of errors today and not
the usual " E:Unable to parse package file..."

Please see the results:

```
root@aria:~# apt-get update
Ign http://archive.ubuntu.com precise InRelease
Ign http://archive.ubuntu.com precise-updates InRelease
Ign http://archive.ubuntu.com precise-backports InRelease
Ign http://archive.ubuntu.com precise-security InRelease
Hit http://archive.ubuntu.com precise Release.gpg
Hit http://archive.ubuntu.com precise-updates Release.gpg
Hit http://archive.ubuntu.com precise-backports Release.gpg
Hit http://archive.ubuntu.com precise-security Release.gpg
Hit http://archive.ubuntu.com precise Release
Hit http://archive.ubuntu.com precise-updates Release
Hit http://archive.ubuntu.com precise-backports Release
Hit http://archive.ubuntu.com precise-security Release
Hit http://archive.ubuntu.com precise/main amd64 Packages
Hit http://archive.ubuntu.com precise/restricted amd64 Packages
Get:1 http://archive.ubuntu.com precise/universe amd64 Packages [429 kB]
Get:2 http://archive.ubuntu.com precise/main i386 Packages [154 kB]
Get:3 http://archive.ubuntu.com precise/restricted i386 Packages [8,366 B]
Get:4 http://archive.ubuntu.com precise/universe i386 Packages [437 kB]                                                                                               
Get:5 http://archive.ubuntu.com precise/main TranslationIndex [155 kB]                                                                                                
Get:6 http://archive.ubuntu.com precise/restricted TranslationIndex [8,374 B]                                                                                         
Get:7 http://archive.ubuntu.com precise/universe TranslationIndex [3,564 B]                                                                                           
Get:8 http://archive.ubuntu.com precise-updates/main amd64 Packages [2,461 B]                                                                                         
86% [8 Packages bzip2 0 B] [Waiting for headers]                                                                                                          98.0 kB/s 1sbzip2: (stdin) is not a bzip2 file.
Get:9 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [2,850 B]                                                                                   
86% [9 Packages bzip2 0 B] [Waiting for headers]                                                                                                          98.0 kB/s 1sbzip2: (stdin) is not a bzip2 file.
Get:10 http://archive.ubuntu.com precise-updates/universe amd64 Packages [1,945 B]                                                                                    
Get:11 http://archive.ubuntu.com precise-updates/main i386 Packages [14 B]                                                                                            
Get:12 http://archive.ubuntu.com precise-updates/restricted i386 Packages [16.7 kB]                                                                                   
Get:13 http://archive.ubuntu.com precise-updates/universe i386 Packages [2,489 B]                                                                                     
Get:14 http://archive.ubuntu.com precise-updates/main TranslationIndex [1,941 B]                                                                                      
Get:15 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [14 B]                                                                                   
Get:16 http://archive.ubuntu.com precise-updates/universe TranslationIndex [16.7 kB]                                                                                  
Get:17 http://archive.ubuntu.com precise-backports/main amd64 Packages [2,504 B]                                                                                      
Get:18 http://archive.ubuntu.com precise-backports/restricted amd64 Packages [72 B]                                                                                   
85% [18 Packages bzip2 0 B] [Waiting for headers]                                                                                                         98.0 kB/s 1sbzip2: (stdin) is not a bzip2 file.
Get:19 http://archive.ubuntu.com precise-backports/universe amd64 Packages [72 B]                                                                                     
85% [19 Packages bzip2 0 B] [Waiting for headers]                                                                                                         98.0 kB/s 1sbzip2: (stdin) is not a bzip2 file.
Get:20 http://archive.ubuntu.com precise-backports/multiverse amd64 Packages [70 B]                                                                                   
85% [20 Packages bzip2 0 B] [Waiting for headers]                                                                                                         98.0 kB/s 1sbzip2: (stdin) is not a bzip2 file.
Get:21 http://archive.ubuntu.com precise-backports/main i386 Packages [73 B]                                                                                          
85% [21 Packages bzip2 0 B] [Waiting for headers]                                                                                                         98.0 kB/s 1sbzip2: (stdin) is not a bzip2 file.
Get:22 http://archive.ubuntu.com precise-backports/restricted i386 Packages [198 kB]                                                                                  
Get:23 http://archive.ubuntu.com precise-backports/universe i386 Packages [55.7 kB]                                                                                   
Get:24 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [3,969 B]                                                                                 
Get:25 http://archive.ubuntu.com precise-backports/main TranslationIndex [2,189 B]                                                                                    
Get:26 http://archive.ubuntu.com precise-backports/multiverse TranslationIndex [204 kB]                                                                               
Get:27 http://archive.ubuntu.com precise-backports/restricted TranslationIndex [56.5 kB]                                                                              
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex                                                                                             
Get:28 http://archive.ubuntu.com precise-security/main amd64 Packages [2,388 B]                                                                                       
Get:29 http://archive.ubuntu.com precise-security/restricted amd64 Packages [73 B]                                                                                    
75% [29 Packages bzip2 0 B] [Waiting for headers]                                                                                                          122 kB/s 3sbzip2: (stdin) is not a bzip2 file.
Get:30 http://archive.ubuntu.com precise-security/universe amd64 Packages [71 B]                                                                                      
75% [30 Packages bzip2 0 B] [Waiting for headers]                                                                                                          122 kB/s 3sbzip2: (stdin) is not a bzip2 file.
Get:31 http://archive.ubuntu.com precise-security/multiverse amd64 Packages [71 B]                                                                                    
75% [31 Packages bzip2 0 B] [Waiting for headers]                                                                                                          122 kB/s 3sbzip2: (stdin) is not a bzip2 file.
Get:32 http://archive.ubuntu.com precise-security/main i386 Packages [73 B]                                                                                           
75% [32 Packages bzip2 0 B] [Waiting for headers]                                                                                                          122 kB/s 3sbzip2: (stdin) is not a bzip2 file.
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages                                                                                               
Get:33 http://archive.ubuntu.com precise-security/universe i386 Packages [553 kB]                                                                                     
81% [33 Packages bzip2 0 B] [Waiting for headers]                                                                                                          122 kB/s 3sbzip2: (stdin) is not a bzip2 file.
Get:34 http://archive.ubuntu.com precise-security/multiverse i386 Packages [20 B]                                                                                     
81% [34 Packages bzip2 0 B] [Waiting for headers]                                                                                                          122 kB/s 3sbzip2: (stdin) is not a bzip2 file.
Get:35 http://archive.ubuntu.com precise-security/main TranslationIndex [8,523 B]                                                                                     
Get:36 http://archive.ubuntu.com precise-security/multiverse TranslationIndex [18.9 kB]                                                                               
Get:37 http://archive.ubuntu.com precise-security/restricted TranslationIndex [2,238 B]                                                                               
Get:38 http://archive.ubuntu.com precise-security/universe TranslationIndex [1,778 B]                                                                                 
Hit http://archive.ubuntu.com precise-updates/main amd64 Packages [2,461 B]                                                                                           
Get:39 http://archive.ubuntu.com precise-backports/universe Translation-en_IN [2,139 B]                                                                               
80% [39 Translation-en_IN bzip2 0 B] [Waiting for headers]                                                                                                91.4 kB/s 5sbzip2: (stdin) is not a bzip2 file.
Err http://archive.ubuntu.com precise-security/restricted amd64 Packages                                                                                              
  404  Not Found
Err http://archive.ubuntu.com precise-security/universe amd64 Packages                                                                                                
  404  Not Found
Err http://archive.ubuntu.com precise-security/multiverse amd64 Packages                                                                                              
  404  Not Found
Err http://archive.ubuntu.com precise-security/main i386 Packages
  404  Not Found
Err http://archive.ubuntu.com precise-security/universe i386 Packages
  404  Not Found
Err http://archive.ubuntu.com precise-security/multiverse i386 Packages
  404  Not Found
Hit http://archive.ubuntu.com precise/universe Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Ign http://archive.ubuntu.com precise-backports/universe Translation-en_IN
Fetched 2,354 kB in 32s (71.9 kB/s)
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages  404  Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages  404  Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by NikTh on 2012-11-20
Hi , 
have you tried to follow the [Package Manager Troubleshooting Procedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure) ? 

Thanks

---

### Post by chetkgp on 2012-11-21
Hi NikTh,

I followed the instructions in the Package Manager trouble shooting
procedure step-by-step. However, when I executed the line

```
LANG=C;sudo apt-get update -o APT::Cache-Limit=100000000
```it gave the same error

```
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

