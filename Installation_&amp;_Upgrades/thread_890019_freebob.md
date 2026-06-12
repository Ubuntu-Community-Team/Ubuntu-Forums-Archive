---
title: "freebob"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by andysking on 2008-08-14
I have been trying to install the latest feebob on 8.04, and keep running into difficulties with the "make" command during installation.  It will give me an error saying that there is nothing to make, what should I do?

---

### Post by Partyboi2 on 2008-08-15
If you are trying to install freebob I think you can install it from the ubuntu repo's via synaptic or terminal.
```
sudo apt-get install libfreebob0
```
If for some reason you need to compile it, have a look at the install or readme file, as this normally will explain how to install.

---

### Post by andysking on 2008-08-15
after trying that I ended up getting this error

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Partyboi2 on 2008-08-15
That happens when synaptic or another package update, installation application is already running. In other words you can only have one package manager running at a time. So make sure you are only using one at a time either synaptic package manager, add/remove or apt-get.

---

### Post by andysking on 2008-08-16
That worked to get rid of the first error, but now I am getting this one. 
```
E: Type '--21:55:33--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

```

Any ideas?

---

### Post by Partyboi2 on 2008-08-16
open a terminal (applications>accessories>terminal) and [FONT=monospace]backup[/FONT][FONT=monospace] the file
[/FONT]```
sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.bak
```then
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by andysking on 2008-08-16
Everything worked until the last string of code when I got this output:

```
Install these packages without verification [y/N]? y
Err http://packages.medibuntu.org hardy/free medibuntu-keyring 2008.04.20
  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Failed to fetch http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by Partyboi2 on 2008-08-17
what happens when you try
```
sudo apt-get update
```

---

### Post by andysking on 2008-08-17
```
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release 
Get:1 http://packages.medibuntu.org hardy Release.gpg [189B]        
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US  
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages                     
Hit http://us.archive.ubuntu.com hardy/main Sources                            
Hit http://us.archive.ubuntu.com hardy/restricted Sources                      
Hit http://us.archive.ubuntu.com hardy/universe Packages                       
Get:2 http://packages.medibuntu.org hardy Release [9335B]                      
Ign http://packages.medibuntu.org hardy Release                                
Hit http://us.archive.ubuntu.com hardy/universe Sources                        
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://us.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://us.archive.ubuntu.com hardy-updates/main Sources                    
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources              
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources              
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Fetched 190B in 6s (30B/s)                                                     
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

---

### Post by Partyboi2 on 2008-08-18
open up a terminal and try reinstalling medibuntu keyring
```
sudo apt-get install --reinstall medibuntu-keyring
```

---

### Post by andysking on 2008-08-18
Ok, this is the output

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  artsbuilder xulrunner-1.9-dom-inspector libmozjs0d
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]? y
Get:1 http://packages.medibuntu.org hardy/free medibuntu-keyring 2008.04.20 [3448B]
Fetched 3448B in 1s (3014B/s)            
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 125223 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

```

Am I good to try that 3rd line of code again?

---

### Post by Partyboi2 on 2008-08-19
> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get updateIf you mean this line, you shouldn't have to as you have just reinstalled the mediubuntu keyring.
Open a terminal and run
```
sudo apt-get update
``` All going well it should be all ok.

---

### Post by andysking on 2008-08-21
ok, thanks

---

