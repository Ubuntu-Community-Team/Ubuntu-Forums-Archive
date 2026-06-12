---
title: "someone advanced &amp; would use Teamviewer"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by AmjAdAsh2Ar on 2012-10-05
[SIZE="2"]Is there someone who is advanced in ubuntu 12.04 & would offer help  using Teamviewer .. I got a serious issue. 

I'm really desperate of searching for solutions. I wasted a lot of time doing that.[/SIZE]

---

### Post by albandy on 2012-10-05
> **AmjAdAsh2Ar said:**
> [SIZE="2"]Is there someone who is advanced in ubuntu 12.04 & would offer help  using Teamviewer .. I got a serious issue. 

I'm really desperate of searching for solutions. I wasted a lot of time doing that.[/SIZE]

before connecting to your computer, can you explain what are the issues?

---

### Post by AmjAdAsh2Ar on 2012-10-06
> **albandy said:**
> before connecting to your computer, can you explain what are the issues?

unmet depedencies
I cant install or remove any software

---

### Post by albandy on 2012-10-06
ok I'll try to help you. Send me a private message with the teamvier code

---

### Post by albandy on 2012-10-08
Open a console and type:
sudo apt-get update, if error occurs post it here.

After this run 
sudo apt-get upgrade
and if error occurs post it here.

---

### Post by AmjAdAsh2Ar on 2012-10-08
amjad@amjad-HP-PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libgcc1 but it is not installed
         Depends: tzdata but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by oldos2er on 2012-10-08
Can you post the results of ```
cat /etc/apt/sources.list
``` ?

---

### Post by albandy on 2012-10-08
> **oldos2er said:**
> Can you post the results of ```
cat /etc/apt/sources.list
``` ?

and the files from /etc/apt/sources.list.d/

---

### Post by AmjAdAsh2Ar on 2012-10-08
```
amjad@amjad-HP-PC:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://jo.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://jo.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://jo.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://jo.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://jo.archive.ubuntu.com/ubuntu/ precise universe
deb http://jo.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://jo.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://jo.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://jo.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://jo.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse #Added by software-properties

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

@albandy : What do u mean by the "files from etc/apt/sources.list" ?? should I copy all the 6 files contents ??
However, these are the files located there , (attached)

---

### Post by AmjAdAsh2Ar on 2012-10-08
I get this when i click repair in the software center
[package operation failed]
```

installArchives() failed: E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 478 files and directories currently installed.)
Preparing to replace libc-bin 2.15-0ubuntu10 (using .../libc-bin_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc-bin ...
Setting up libc-bin (2.15-0ubuntu10.2) ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 478 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10 (using .../libc6_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: regarding .../libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb containing libgcc1, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.
dpkg: error processing /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb (--unpack):
 pre-dependency problem - not installing libgcc1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/libgcc1_1%3a4.6.3-1ubuntu5_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on libgcc1; however:
  Package libgcc1 is not installed.
 libc6 depends on tzdata; however:
  Package tzdata is not installed.
dpkg: error processing libc6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.3.6-2); however:
  Package libc6 is not configured yet.
dpkg: error processing multiarch-support (--configure):
 dependency problems - leaving unconfigured

```

---

### Post by oldos2er on 2012-10-08
Your sources look ok. Try clearing your apt cache: ```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by AmjAdAsh2Ar on 2012-10-08
> **oldos2er said:**
> Your sources look ok. Try clearing your apt cache: ```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

```
amjad@amjad-HP-PC:~$ sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
[sudo] password for amjad: 
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://extras.ubuntu.com precise Release.gpg                               
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://archive.ubuntu.com precise Release.gpg                              
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://extras.ubuntu.com precise Release                                   
Get:2 http://dl.google.com stable Release [1,347 B]                            
Hit http://archive.ubuntu.com precise Release                                  
Hit http://security.ubuntu.com precise-security Release                        
Hit http://extras.ubuntu.com precise/main Sources                              
Get:3 http://dl.google.com stable/main amd64 Packages [1,226 B]                
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:4 http://dl.google.com stable/main i386 Packages [1,230 B]                 
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://security.ubuntu.com precise-security/main Sources                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/main amd64 Packages            
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages      
Hit http://security.ubuntu.com precise-security/universe amd64 Packages        
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Ign http://jo.archive.ubuntu.com precise InRelease                             
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Ign http://archive.canonical.com precise InRelease                             
Ign http://jo.archive.ubuntu.com precise-updates InRelease                     
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://ppa.launchpad.net precise Release                                   
Get:5 http://archive.canonical.com precise Release.gpg [198 B]                 
Ign http://jo.archive.ubuntu.com precise-backports InRelease                   
Hit http://ppa.launchpad.net precise/main Sources                              
Get:6 http://archive.canonical.com precise Release [7,078 B]                   
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://jo.archive.ubuntu.com precise Release.gpg                           
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://jo.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://jo.archive.ubuntu.com precise-backports Release.gpg                 
Get:7 http://archive.canonical.com precise/partner i386 Packages [5,016 B]     
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://jo.archive.ubuntu.com precise Release                               
Hit http://jo.archive.ubuntu.com precise-updates Release                       
Hit http://jo.archive.ubuntu.com precise-backports Release                     
Hit http://jo.archive.ubuntu.com precise/restricted Sources                    
Hit http://jo.archive.ubuntu.com precise/main Sources                          
Hit http://jo.archive.ubuntu.com precise/multiverse Sources                    
Hit http://jo.archive.ubuntu.com precise/universe Sources                      
Hit http://jo.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://jo.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://jo.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://jo.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://jo.archive.ubuntu.com precise/main i386 Packages                    
Hit http://jo.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://jo.archive.ubuntu.com precise/universe i386 Packages                
Hit http://jo.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://jo.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://jo.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://jo.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://jo.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://jo.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://jo.archive.ubuntu.com precise-updates/main Sources                  
Hit http://jo.archive.ubuntu.com precise-updates/multiverse Sources            
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://jo.archive.ubuntu.com precise-updates/universe Sources              
Hit http://jo.archive.ubuntu.com precise-updates/main amd64 Packages           
Hit http://jo.archive.ubuntu.com precise-updates/restricted amd64 Packages     
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://jo.archive.ubuntu.com precise-updates/universe amd64 Packages       
Ign http://dl.google.com stable/main Translation-en                            
Hit http://jo.archive.ubuntu.com precise-updates/multiverse amd64 Packages     
Hit http://jo.archive.ubuntu.com precise-updates/main i386 Packages   
Hit http://jo.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://jo.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://jo.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://jo.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://jo.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://jo.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://jo.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://jo.archive.ubuntu.com precise-backports/main Sources       
Hit http://jo.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://jo.archive.ubuntu.com precise-backports/universe Sources            
Hit http://jo.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://jo.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://jo.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://jo.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://jo.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://jo.archive.ubuntu.com precise-backports/main i386 Packages 
Hit http://jo.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://jo.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://jo.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://jo.archive.ubuntu.com precise-backports/main TranslationIndex   
Hit http://jo.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://jo.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://jo.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://jo.archive.ubuntu.com precise/main Translation-en                   
Hit http://jo.archive.ubuntu.com precise/multiverse Translation-en    
Hit http://jo.archive.ubuntu.com precise/restricted Translation-en    
Hit http://jo.archive.ubuntu.com precise/universe Translation-en      
Hit http://jo.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://jo.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://jo.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://jo.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://jo.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://jo.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://jo.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://jo.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Fetched 16.3 kB in 13s (1,249 B/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libgcc1 but it is not installed
         Depends: tzdata but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by drdos2006 on 2012-10-08
The error message you are getting says run this command,

sudo apt-get -f install

to correct the dependicies.

regards

---

### Post by AmjAdAsh2Ar on 2012-10-08
> **drdos2006 said:**
> The error message you are getting says run this command,

sudo apt-get -f install

to correct the dependicies.

regards
that doesn't work. Because after finishing downloading the packages, it brings the same error

---

### Post by vandorjw on 2012-10-08
run the following and tell me your results

Step 1.
```

sudo dpkg --configure multiarch-support

```

Alternative to step 1
```

dpkg --configure -a

```

Step 2.
```

sudo apt-get install libgcc1 tzdata

```

If step1 gave you errors, try step 2, then step 1 again.

If for some-reason, apt-get doesn't let you download and install libgcc1 and tzdata, then download them from here:
[http://mirrors.us.kernel.org/ubuntu//pool/main/g/gcc-4.6/libgcc1_4.6.3-1ubuntu5_amd64.deb](http://mirrors.us.kernel.org/ubuntu//pool/main/g/gcc-4.6/libgcc1_4.6.3-1ubuntu5_amd64.deb)

and here:
[http://security.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2012e-0ubuntu0.12.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2012e-0ubuntu0.12.04.1_all.deb)

After downloading, run

sudo dpkg -i "file_name.deb"

-------------------------
**STEP BY STEP INSTRUCTIONS**
--------------------------

If you wish, follow these exact instructions to the letter.
Open the terminal, and type the following commands, in order they are given.
Where I said to give your password, give the password, and don't type "give password"
Do not enter "$", it just signals a new instruction to follow.
```

$ cd ~
$ wget http://security.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2012e-0ubuntu0.12.04.1_all.deb
$ wget http://mirrors.us.kernel.org/ubuntu//pool/main/g/gcc-4.6/libgcc1_4.6.3-1ubuntu5_amd64.deb
$ sudo dpkg -i ~/tzdata_2012e-0ubuntu0.12.04.1_all.deb
$ "enter password"
$ sudo dpkg -i ~/libgcc1_4.6.3-1ubuntu5_amd64.deb
$ "enter your password again"
$ sudo dpkg --configure -a
$ sudo apt-get update && sudo apt-get upgrade

```

Everything should work again now.

---

### Post by drdos2006 on 2012-10-08
In that case, if it was my machine, I would do a complete re-install.

Before doing a complete re-install, I would remove the cover from my desktop and re-insert memory, re-insert hard drives cables, PCI cards etc, but if you have a laptop, then I would use the live CD to at least check the memory.

regards

---

### Post by AmjAdAsh2Ar on 2012-10-09
@cc7gir
I tried the first steps and unfortunately these are the results :
```
[COLOR="Red"]amjad@amjad-HP-PC:~$[/COLOR] sudo dpkg --configure multiarch-support
[sudo] password for amjad: 
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.3.6-2); however:
  Package libc6 is not configured yet.
dpkg: error processing multiarch-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 multiarch-support
[COLOR="red"]amjad@amjad-HP-PC:~$[/COLOR] dpkg --configure -a
dpkg: error: requested operation requires superuser privilege
-------------------------------
[COLOR="red"]amjad@amjad-HP-PC:~$[/COLOR] sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on libgcc1; however:
  Package libgcc1 is not installed.
 libc6 depends on tzdata; however:
  Package tzdata is not installed.
dpkg: error processing libc6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.3.6-2); however:
  Package libc6 is not configured yet.
dpkg: error processing multiarch-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6
 multiarch-support
--------------------------------
[COLOR="red"]amjad@amjad-HP-PC:~$[/COLOR] sudo apt-get install libgcc1 tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 tzdata : Depends: debconf (>= 0.5) but it is not going to be installed or
                   debconf-2.0
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
and then ... 
```
[COLOR="red"]amjad@amjad-HP-PC:~$[/COLOR] sudo dpkg -i "/home/amjad/Desktop/libgcc1_4.6.3-1ubuntu5_amd64.deb"
dpkg: regarding .../libgcc1_4.6.3-1ubuntu5_amd64.deb containing libgcc1, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.
dpkg: error processing /home/amjad/Desktop/libgcc1_4.6.3-1ubuntu5_amd64.deb (--install):
 pre-dependency problem - not installing libgcc1
Errors were encountered while processing:
 /home/amjad/Desktop/libgcc1_4.6.3-1ubuntu5_amd64.deb
[COLOR="red"]amjad@amjad-HP-PC:~$[/COLOR] sudo dpkg -i "/home/amjad/Desktop/tzdata_2012e-0ubuntu0.12.04.1_all.deb"
Selecting previously unselected package tzdata.
(Reading database ... 478 files and directories currently installed.)
Unpacking tzdata (from .../tzdata_2012e-0ubuntu0.12.04.1_all.deb) ...
dpkg: dependency problems prevent configuration of tzdata:
 tzdata depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not installed.
  Package debconf-2.0 is not installed.
dpkg: error processing tzdata (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
```

after that ,, I followed the "step by step instructions" and got the same results, here : 
```

[COLOR="Red"]amjad@amjad-HP-PC:~$[/COLOR]  cd ~
[COLOR="red"]amjad@amjad-HP-PC:~$[/COLOR] wget http://security.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2012e-0ubuntu0.12.04.1_all.deb
--2012-10-09 08:56:50--  http://security.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2012e-0ubuntu0.12.04.1_all.deb
Resolving security.ubuntu.com (security.ubuntu.com)... 91.189.92.190, 91.189.92.184
Connecting to security.ubuntu.com (security.ubuntu.com)|91.189.92.190|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 474432 (463K) [application/x-debian-package]
Saving to: `tzdata_2012e-0ubuntu0.12.04.1_all.deb'

100%[==============================>] 474,432      236K/s   in 2.0s    

2012-10-09 08:56:52 (236 KB/s) - `tzdata_2012e-0ubuntu0.12.04.1_all.deb' saved [474432/474432]

[COLOR="red"]amjad@amjad-HP-PC:~$[/COLOR] wget http://mirrors.us.kernel.org/ubuntu//pool/main/g/gcc-4.6/libgcc1_4.6.3-1ubuntu5_amd64.deb
--2012-10-09 08:57:15--  http://mirrors.us.kernel.org/ubuntu//pool/main/g/gcc-4.6/libgcc1_4.6.3-1ubuntu5_amd64.deb
Resolving mirrors.us.kernel.org (mirrors.us.kernel.org)... 149.20.4.71
Connecting to mirrors.us.kernel.org (mirrors.us.kernel.org)|149.20.4.71|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 42608 (42K) [text/plain]
Saving to: `libgcc1_4.6.3-1ubuntu5_amd64.deb'

100%[==============================>] 42,608       203K/s   in 0.2s    

2012-10-09 08:57:16 (203 KB/s) - `libgcc1_4.6.3-1ubuntu5_amd64.deb' saved [42608/42608]

[COLOR="red"]amjad@amjad-HP-PC:~$[/COLOR] sudo dpkg -i ~/tzdata_2012e-0ubuntu0.12.04.1_all.deb
[sudo] password for amjad: 
(Reading database ... 2341 files and directories currently installed.)
Preparing to replace tzdata 2012e-0ubuntu0.12.04.1 (using .../tzdata_2012e-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement tzdata ...
dpkg: dependency problems prevent configuration of tzdata:
 tzdata depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not installed.
  Package debconf-2.0 is not installed.
dpkg: error processing tzdata (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
[COLOR="red"]amjad@amjad-HP-PC:~$[/COLOR] sudo dpkg -i ~/libgcc1_4.6.3-1ubuntu5_amd64.deb
dpkg: regarding .../libgcc1_4.6.3-1ubuntu5_amd64.deb containing libgcc1, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.
dpkg: error processing /home/amjad/libgcc1_4.6.3-1ubuntu5_amd64.deb (--install):
 pre-dependency problem - not installing libgcc1
Errors were encountered while processing:
 /home/amjad/libgcc1_4.6.3-1ubuntu5_amd64.deb
[COLOR="red"]amjad@amjad-HP-PC:~$[/COLOR] sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of tzdata:
 tzdata depends on debconf (>= 0.5) | debconf-2.0; however:
  Package debconf is not installed.
  Package debconf-2.0 is not installed.
dpkg: error processing tzdata (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on libgcc1; however:
  Package libgcc1 is not installed.
 libc6 depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing libc6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.3.6-2); however:
  Package libc6 is not configured yet.
dpkg: error processing multiarch-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 libc6
 multiarch-support
[COLOR="red"]amjad@amjad-HP-PC:~$[/COLOR] sudo apt-get update && sudo apt-get upgrade
Ign http://security.ubuntu.com precise-security InRelease
Ign http://dl.google.com stable InRelease                              
Ign http://archive.ubuntu.com precise InRelease                        
Ign http://extras.ubuntu.com precise InRelease                         
Ign http://jo.archive.ubuntu.com precise InRelease                     
Hit http://security.ubuntu.com precise-security Release.gpg            
Ign http://archive.canonical.com precise InRelease                     
Ign http://ppa.launchpad.net precise InRelease                         
Get:1 http://dl.google.com stable Release.gpg [198 B]                  
Hit http://archive.ubuntu.com precise Release.gpg                      
Hit http://security.ubuntu.com precise-security Release                
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]              
Ign http://jo.archive.ubuntu.com precise-updates InRelease             
Get:3 http://dl.google.com stable Release [1,347 B]                    
Hit http://archive.canonical.com precise Release.gpg                   
Hit http://ppa.launchpad.net precise Release.gpg                       
Hit http://archive.ubuntu.com precise Release                          
Hit http://extras.ubuntu.com precise Release                           
Hit http://archive.canonical.com precise Release                       
Hit http://ppa.launchpad.net precise Release                           
Hit http://security.ubuntu.com precise-security/restricted Sources     
Ign http://jo.archive.ubuntu.com precise-backports InRelease           
Get:4 http://dl.google.com stable/main amd64 Packages [1,223 B]        
Hit http://extras.ubuntu.com precise/main Sources                      
Hit http://archive.ubuntu.com precise/main Sources                     
Hit http://security.ubuntu.com precise-security/main Sources           
Hit http://archive.canonical.com precise/partner amd64 Packages        
Hit http://ppa.launchpad.net precise/main Sources                      
Hit http://security.ubuntu.com precise-security/multiverse Sources     
Get:5 http://dl.google.com stable/main i386 Packages [1,224 B]         
Hit http://extras.ubuntu.com precise/main amd64 Packages               
Hit http://archive.ubuntu.com precise/restricted Sources               
Hit http://jo.archive.ubuntu.com precise Release.gpg                   
Hit http://security.ubuntu.com precise-security/universe Sources       
Ign http://dl.google.com stable/main TranslationIndex                  
Hit http://archive.canonical.com precise/partner i386 Packages         
Hit http://extras.ubuntu.com precise/main i386 Packages                
Hit http://jo.archive.ubuntu.com precise-updates Release.gpg           
Hit http://ppa.launchpad.net precise/main amd64 Packages               
Hit http://security.ubuntu.com precise-security/main amd64 Packages    
Ign http://archive.canonical.com precise/partner TranslationIndex      
Ign http://extras.ubuntu.com precise/main TranslationIndex             
Hit http://ppa.launchpad.net precise/main i386 Packages                
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://jo.archive.ubuntu.com precise-backports Release.gpg         
Ign http://ppa.launchpad.net precise/main TranslationIndex             
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://jo.archive.ubuntu.com precise Release                       
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://jo.archive.ubuntu.com precise-updates Release               
Hit http://security.ubuntu.com precise-security/main i386 Packages     
Hit http://jo.archive.ubuntu.com precise-backports Release             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://jo.archive.ubuntu.com precise/restricted Sources            
Hit http://security.ubuntu.com precise-security/universe i386 Packages 
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://jo.archive.ubuntu.com precise/main Sources                  
Hit http://security.ubuntu.com precise-security/main TranslationIndex  
Hit http://jo.archive.ubuntu.com precise/multiverse Sources            
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://jo.archive.ubuntu.com precise/universe Sources              
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://jo.archive.ubuntu.com precise/main amd64 Packages           
Hit http://security.ubuntu.com precise-security/main Translation-en    
Hit http://jo.archive.ubuntu.com precise/restricted amd64 Packages     
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://jo.archive.ubuntu.com precise/universe amd64 Packages       
Hit http://jo.archive.ubuntu.com precise/multiverse amd64 Packages     
Hit http://jo.archive.ubuntu.com precise/main i386 Packages            
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://jo.archive.ubuntu.com precise/restricted i386 Packages      
Hit http://jo.archive.ubuntu.com precise/universe i386 Packages        
Hit http://jo.archive.ubuntu.com precise/multiverse i386 Packages      
Hit http://jo.archive.ubuntu.com precise/main TranslationIndex         
Hit http://jo.archive.ubuntu.com precise/multiverse TranslationIndex   
Hit http://jo.archive.ubuntu.com precise/restricted TranslationIndex   
Hit http://jo.archive.ubuntu.com precise/universe TranslationIndex     
Hit http://jo.archive.ubuntu.com precise-updates/restricted Sources    
Hit http://jo.archive.ubuntu.com precise-updates/main Sources          
Hit http://jo.archive.ubuntu.com precise-updates/multiverse Sources    
Hit http://jo.archive.ubuntu.com precise-updates/universe Sources      
Hit http://jo.archive.ubuntu.com precise-updates/main amd64 Packages   
Hit http://jo.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://jo.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://jo.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Ign http://extras.ubuntu.com precise/main Translation-en_US            
Hit http://jo.archive.ubuntu.com precise-updates/main i386 Packages    
Ign http://extras.ubuntu.com precise/main Translation-en               
Hit http://jo.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://jo.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://jo.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://jo.archive.ubuntu.com precise-updates/main TranslationIndex 
Hit http://jo.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://jo.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://jo.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://jo.archive.ubuntu.com precise-backports/main Sources        
Hit http://jo.archive.ubuntu.com precise-backports/restricted Sources  
Hit http://jo.archive.ubuntu.com precise-backports/universe Sources    
Hit http://jo.archive.ubuntu.com precise-backports/multiverse Sources  
Ign http://dl.google.com stable/main Translation-en_US                 
Hit http://jo.archive.ubuntu.com precise-backports/main amd64 Packages 
Hit http://jo.archive.ubuntu.com precise-backports/restricted amd64 Packages
Ign http://archive.canonical.com precise/partner Translation-en_US     
Hit http://jo.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://jo.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Ign http://dl.google.com stable/main Translation-en                    
Hit http://jo.archive.ubuntu.com precise-backports/main i386 Packages  
Hit http://jo.archive.ubuntu.com precise-backports/restricted i386 Packages
Ign http://archive.canonical.com precise/partner Translation-en        
Hit http://jo.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://jo.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://jo.archive.ubuntu.com precise-backports/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en_US
Hit http://jo.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://jo.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://jo.archive.ubuntu.com precise-backports/universe TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://jo.archive.ubuntu.com precise/main Translation-en
Hit http://jo.archive.ubuntu.com precise/multiverse Translation-en
Hit http://jo.archive.ubuntu.com precise/restricted Translation-en
Hit http://jo.archive.ubuntu.com precise/universe Translation-en
Hit http://jo.archive.ubuntu.com precise-updates/main Translation-en
Hit http://jo.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://jo.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://jo.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://jo.archive.ubuntu.com precise-backports/main Translation-en
Hit http://jo.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://jo.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://jo.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 4,064 B in 5s (733 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libgcc1 but it is not installed
 tzdata : Depends: debconf (>= 0.5) but it is not installed or
                   debconf-2.0
E: Unmet dependencies. Try using -f.

```
I hope you still have more Ideas , solutions :D

---

### Post by vandorjw on 2012-10-09
How in the world did you get to this state?

You are in a loop,
tzdata requires debconf --> debconf requires perl-base --> perl-base requires libc6 --> libc6 requires tzdata

My next try would be to force an install of libc6
sudo apt-get install -f libc6

then hopefully perl-base will install without issues, which will allow debconf, which should allow tzdata.

But then there are still other dependancy cycles left.

If you want to try and fix your system, could you attached a list of installed packages?

Generate using
```

dpkg --list > ~/installed_package_list.txt

```

The contents should have a simular structure as what I have attached to this message.

Otherwise, it will likely be simpler to start over and re-install.

---

### Post by SlugSlug on 2012-10-09
I'd go for aptitude

```
sudo apt-get install aptitude 
```


```
sudo aptitude reinstall libc6 tzdata
```

---

### Post by AmjAdAsh2Ar on 2012-10-09
same problems and errors using force install (_sudo apt-get install -f libc6_)
How  could I attach a list of installed packages?
The code _dpkg --list > ~/installed_package_list.txt_ does nothing.

---

### Post by AmjAdAsh2Ar on 2012-10-09
> **SlugSlug said:**
> I'd go for aptitude
```
sudo apt-get install aptitude 
```
```
sudo aptitude reinstall libc6 tzdata
```

This is the results of these two commands ,, thanks anyways :(

```
amjad@amjad-HP-PC:~$ sudo apt-get install aptitude
[sudo] password for amjad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude : Depends: libapt-pkg4.12 (>= 0.8.16~exp12ubuntu6) but it is not going to be installed
            Depends: libboost-iostreams1.46.1 (>= 1.46.1-1) but it is not going to be installed
            Depends: libcwidget3 but it is not going to be installed
            Depends: libept1.4.12 but it is not going to be installed
            Depends: libgcc1 (>= 1:4.1.1) but it is not going to be installed
            Depends: libncursesw5 (>= 5.6+20070908) but it is not going to be installed
            Depends: libsigc++-2.0-0c2a (>= 2.0.2) but it is not going to be installed
            Depends: libsqlite3-0 (>= 3.6.5) but it is not going to be installed
            Depends: libstdc++6 (>= 4.6) but it is not going to be installed
            Depends: libtinfo5 but it is not going to be installed
            Depends: libxapian22 but it is not going to be installed
            Recommends: sensible-utils but it is not going to be installed
            Recommends: apt-xapian-index but it is not going to be installed
            Recommends: libparse-debianchangelog-perl but it is not going to be installed
 libc6 : Depends: libgcc1 but it is not going to be installed
 tzdata : Depends: debconf (>= 0.5) but it is not going to be installed or
                   debconf-2.0
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
amjad@amjad-HP-PC:~$ sudo aptitude reinstall libc6 tzdata
sudo: aptitude: command not found
amjad@amjad-HP-PC:~$ 

```

---

### Post by AmjAdAsh2Ar on 2012-10-09
> **cc7gir said:**
> How in the world did you get to this state?

I know the bad thing I did. 
I'm fresh to Ubuntu .,, I'm using a labtop, I loved it, but I hate the touchpad's functionality , I can NOT click a right click .. so I googled that, and finished with the stupid solution that got me into this situation which is adding a file named :
"50-synaptics.conf.d" to this location "/usr/share/X11/xorg.conf.d"

after that I restarted the system .. and everything was crashed .. I couldn't login ( just black screen) I only could use SUDO (using my password)
then, I googled how to delete a file using SUDO .. and I did delete this stupid file "50-synaptics.conf.d" .. and then reboot the system .. and this is how I got the red stop button saying :```
 An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The
     error message was "Error: BrokenCount >0". This usually means that your installed packages have unmet dependencies.
```
and that was my story ,, I hope that there would be another solution to reinstalling the system.

---

### Post by josephmills on 2012-10-09
Ive got a hour or two that I can burn on debuging and setting up these dependence errors. Send me a pm with teamviewer info. Also if you can click on the link in my signature and sign into that. My name on IRC is bobweaver Just ask for me and I will respond.

---

### Post by AmjAdAsh2Ar on 2012-10-09
**THE SOLUTION IS A RE-INSTALLATION (BAD SECTORS IN THE HARDDRIVE IS THE CAUSE OF THIS MESS) MUCH THANKS FOR 'josephmills'**
AND FOR ALL THE PEOPLE WHO TRIED TO SOLVE MY PROBLEM :)

---

