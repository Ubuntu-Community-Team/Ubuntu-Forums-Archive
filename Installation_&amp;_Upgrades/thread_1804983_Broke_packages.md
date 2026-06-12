---
title: "Broke packages"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by collinge on 2011-07-15
I get this anytime i do anything like goto software center and S.P.M.

```

collinge@collinge-PW504AA-ABA-SR1429NX-NA520:~$ sudo apt-get upgrade
[sudo] password for collinge: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.
collinge@collinge-PW504AA-ABA-SR1429NX-NA520:~$ 

```




i was trying to install a prog last night... 
[http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice]("http://www.synce.org/moin/SynceInstallation/Ubuntu/ModernDevice")

I followed the directions... 
then for trouble shooting i went here

[http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)
.. no luck 

even tried this... with no luck..
```

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```


i edited the source list and removed the two lines i added and updated and still nothing... 

here is my list..


```
collinge@collinge-PW504AA-ABA-SR1429NX-NA520:~$ cd /var/lib/apt/lists/
collinge@collinge-PW504AA-ABA-SR1429NX-NA520:/var/lib/apt/lists$ ls
archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages
archive.canonical.com_ubuntu_dists_natty_Release
archive.canonical.com_ubuntu_dists_natty_Release.gpg
extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
extras.ubuntu.com_ubuntu_dists_natty_main_source_Sources
extras.ubuntu.com_ubuntu_dists_natty_Release
extras.ubuntu.com_ubuntu_dists_natty_Release.gpg
lock
partial
security.ubuntu.com_ubuntu_dists_natty-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources
security.ubuntu.com_ubuntu_dists_natty-security_Release
security.ubuntu.com_ubuntu_dists_natty-security_Release.gpg
security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources
security.ubuntu.com_ubuntu_dists_natty-security_universe_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_Release
us.archive.ubuntu.com_ubuntu_dists_natty_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release
us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Translation-en%5fUS
us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources

```

.. also.. how do u change your "computer name" mine is PW504AA-ABA-SR1429NX-NA520



thanks guys... cant wait for the intel bugs to get fixed

---

### Post by Ad@m on 2011-07-15
Try this instead,

sudo rm /var/lib/apt/lists/*
sudo apt-get update

And to change your hostname

sudo hostname ***whatever***

---

### Post by collinge on 2011-07-15
```
 sudo rm /var/lib/apt/lists/*
[sudo] password for collinge: 
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

```

---

### Post by Ad@m on 2011-07-15
Don't  worry about the error message concerning the partial directory.

Does **sudo apt-get update** now work?

---

### Post by collinge on 2011-07-15
nope

---

### Post by collinge on 2011-07-15
```
 sudo apt-get update
Ign http://extras.ubuntu.com natty InRelease                                   
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]                        
Get:2 http://extras.ubuntu.com natty Release [9,753 B]                         
Get:3 http://extras.ubuntu.com natty/main Sources [14 B]                       
Ign http://archive.canonical.com natty InRelease                               
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://us.archive.ubuntu.com natty InRelease                               
Get:4 http://extras.ubuntu.com natty/main i386 Packages [14 B]                 
Get:5 http://archive.canonical.com natty Release.gpg [198 B]                   
Get:6 http://security.ubuntu.com natty-security Release.gpg [198 B]            
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Get:7 http://security.ubuntu.com natty-security Release [27.2 kB]              
Get:8 http://archive.canonical.com natty Release [5,916 B]                     
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Get:9 http://archive.canonical.com natty/partner i386 Packages [7,861 B]       
Get:10 http://security.ubuntu.com natty-security/main Sources [59.2 kB]        
Ign http://archive.canonical.com natty/partner TranslationIndex                
Get:11 http://us.archive.ubuntu.com natty Release.gpg [198 B]                  
Get:12 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]          
Get:13 http://security.ubuntu.com natty-security/restricted Sources [14 B]     
Get:14 http://us.archive.ubuntu.com natty Release [39.8 kB]                    
Get:15 http://security.ubuntu.com natty-security/universe Sources [7,103 B]    
Get:16 http://us.archive.ubuntu.com natty-updates Release [27.2 kB]            
Get:17 http://security.ubuntu.com natty-security/multiverse Sources [658 B]    
Get:18 http://security.ubuntu.com natty-security/main i386 Packages [153 kB]   
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Get:19 http://security.ubuntu.com natty-security/restricted i386 Packages [14 B]
Ign http://extras.ubuntu.com natty/main Translation-en                         
Get:20 http://us.archive.ubuntu.com natty/main Sources [862 kB]                
Get:21 http://security.ubuntu.com natty-security/universe i386 Packages [22.0 kB]
Ign http://archive.canonical.com natty/partner Translation-en_US               
Get:22 http://security.ubuntu.com natty-security/multiverse i386 Packages [2,074 B]
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Get:23 http://us.archive.ubuntu.com natty/restricted Sources [4,104 B]         
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Get:24 http://us.archive.ubuntu.com natty/universe Sources [4,380 kB]          
Get:25 http://security.ubuntu.com natty-security/universe Translation-en       
76% [25 Translation-en bzip2 0 B] [24 Sources 3,038 kB/4,380 kB 69%] [Connectinbzip2: (stdin) is not a bzip2 file.
Get:26 http://us.archive.ubuntu.com natty/multiverse Sources [155 kB]          
Get:27 http://us.archive.ubuntu.com natty/main i386 Packages [1,550 kB]        
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Get:28 http://us.archive.ubuntu.com natty/restricted i386 Packages [8,986 B]   
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Get:29 http://security.ubuntu.com natty-security/restricted Translation-en_US  
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Get:30 http://us.archive.ubuntu.com natty/universe i386 Packages [6,021 kB]    
Get:31 http://us.archive.ubuntu.com natty/multiverse i386 Packages [183 kB]    
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Get:32 http://us.archive.ubuntu.com natty-updates/main Sources [94.1 kB]       
Get:33 http://us.archive.ubuntu.com natty-updates/restricted Sources [14 B]    
Get:34 http://us.archive.ubuntu.com natty-updates/universe Sources [17.9 kB]   
Get:35 http://us.archive.ubuntu.com natty-updates/multiverse Sources [1,893 B] 
Get:36 http://us.archive.ubuntu.com natty-updates/main i386 Packages [275 kB]  
Get:37 http://us.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Get:38 http://us.archive.ubuntu.com natty-updates/universe i386 Packages [68.4 kB]
Get:39 http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages [4,267 B]
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Get:40 http://us.archive.ubuntu.com natty/universe Translation-en_US           
99% [40 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:41 http://us.archive.ubuntu.com natty/restricted Translation-en_US         
99% [41 Translation-en_US lzma 0 B] [Waiting for headers]/usr/bin/lzma: Decoder error
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Get:42 http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Fetched 14.0 MB in 5min 14s (44.5 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.
collinge@collinge-PW504AA-ABA-SR1429NX-NA520:~$ 

```


also sudo hostname ..doesnt do anything

---

### Post by Ad@m on 2011-07-15
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/735491](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/735491)

Maybe the above will be of help.

You have to logout/login for the hostname to take effect.

---

### Post by collinge on 2011-07-15
okay.. ive tried everything on that page im still getting 


```
                                        
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.

```

---

### Post by collinge on 2011-07-15
now when i try to manual edit the list i get this.... 

```

sudo gedit /etc/apt/sources.list
[sudo] password for collinge: 
No protocol specified

(gedit:19812): Gtk-WARNING **: cannot open display: :0.0

```

what am i doing wrong

---

### Post by collinge on 2011-07-16
still not working... I cant install .deb packages either... I can now bring up the software sources screen, is there a check box i can undo that might help.... i tried unchecking one waiting a while and checking again to try and get it to reload but it says check your Internet connection..

oh and i can edit etc/apt/sorces.list now

anything?

Thank you for your replies everyone.

---

### Post by collinge on 2011-07-16
yea!! i got it to work... 
I used the following codes

```

Sudo rm /var/lib/apt/lists/partial/*
Sudo rm /var/lib/apt/lists/*
Sudo apt-get update 

```
I unchecked multiverse from source list and was able to reload.

---

### Post by Old_Grey_Wolf on 2011-07-16
> **collinge said:**
> now when i try to manual edit the list i get this.... 

```

sudo gedit /etc/apt/sources.list
[sudo] password for collinge: 
No protocol specified

(gedit:19812): Gtk-WARNING **: cannot open display: :0.0

```

what am i doing wrong

I see you solved the problem; however, were you using ssh to connect to the computer? If so you need to set the environment variable DISPLAY and use ssh -X. To set the environment variable enter ```
export DISPLAY=<your IP>:0.0
```

---

