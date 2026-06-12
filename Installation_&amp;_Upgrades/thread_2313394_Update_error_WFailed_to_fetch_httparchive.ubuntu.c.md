---
title: "Update error: W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/Release"
date: 2016-02-12
forum: Installation &amp; Upgrades
---

### Post by zanog.b on 2016-02-12
```

Get:24 http://archive.ubuntu.com trusty-security/universe Translation-en [72.1 kB]
Get:25 http://archive.ubuntu.com trusty/main Sources [1,064 kB]                
Fetched 1,787 kB in 9s (193 kB/s)                                              
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Hi,

Have been getting above error since few weeks and still persisting. Is there a way to sort out this issue?  I have tried few 'google searches' suggestions but error persists. Could anyone provide me with some guidance please?




cat /etc/apt/sources.list

```
# deb cdrom:[Lubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu trusty main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu trusty universe
deb-src http://archive.ubuntu.com/ubuntu trusty universe
deb http://archive.ubuntu.com/ubuntu trusty-updates universe
deb-src http://archive.ubuntu.com/ubuntu trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu trusty multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty multiverse
deb http://archive.ubuntu.com/ubuntu trusty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb http://archive.ubuntu.com/ubuntu trusty-security universe
deb-src http://archive.ubuntu.com/ubuntu trusty-security universe
deb http://archive.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main
```

sudo apt-get update

```
Ign http://archive.ubuntu.com trusty InRelease
Get:1 http://archive.ubuntu.com trusty-updates InRelease [65.9 kB]
Hit http://archive.ubuntu.com trusty-backports InRelease
Get:2 http://archive.ubuntu.com trusty-security InRelease [65.9 kB]
Hit http://archive.ubuntu.com trusty Release.gpg     
Hit http://archive.ubuntu.com trusty-updates/main Sources
Get:3 http://archive.ubuntu.com trusty-updates/restricted Sources [5,342 B]
Hit http://archive.ubuntu.com trusty-updates/universe Sources      
Get:4 http://archive.ubuntu.com trusty-updates/multiverse Sources [5,547 B]
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages 
Get:5 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [16.0 kB]
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages 
Get:6 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages      
Get:7 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [15.7 kB]
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages  
Get:8 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.4 kB]
Hit http://archive.ubuntu.com trusty-updates/main Translation-en     
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://archive.ubuntu.com trusty-backports/main Sources                    
Hit http://archive.ubuntu.com trusty-backports/restricted Sources              
Hit http://archive.ubuntu.com trusty-backports/universe Sources                
Hit http://archive.ubuntu.com trusty-backports/multiverse Sources              
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages             
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages         
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages       
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages              
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages          
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/main Translation-en             
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en       
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en         
Get:9 http://archive.ubuntu.com trusty-security/main Sources [103 kB]          
Get:10 http://archive.ubuntu.com trusty-security/restricted Sources [4,035 B]  
Get:11 http://archive.ubuntu.com trusty-security/universe Sources [33.0 kB]    
Get:12 http://archive.ubuntu.com trusty-security/multiverse Sources [2,767 B]  
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages              
Get:13 http://archive.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:14 http://archive.ubuntu.com trusty-security/universe amd64 Packages [123 kB]
Get:15 http://archive.ubuntu.com trusty-security/multiverse amd64 Packages [4,990 B]
Hit http://archive.ubuntu.com trusty-security/main i386 Packages               
Get:16 http://archive.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:17 http://archive.ubuntu.com trusty-security/universe i386 Packages [123 kB]
Get:18 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [5,164 B]
Hit http://archive.ubuntu.com trusty-security/main Translation-en              
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en        
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en        
Get:19 http://archive.ubuntu.com trusty-security/universe Translation-en [72.1 kB]
Get:20 http://archive.ubuntu.com trusty Release [11.9 kB]                      
Get:21 http://archive.ubuntu.com trusty/main Sources [14 B]                    
Fetched 710 kB in 18s (37.9 kB/s)                                              
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.




```

---

### Post by v3.xx on 2016-02-12
Try this

Open up your sources list

```
software-properties-gtk
```

and click on "source code" until it appears unchecked, then close and update.

[ATTACH=CONFIG]267249[/ATTACH]

---

### Post by zanog.b on 2016-02-12
Hi v3.xx

Thank you for replying.  Have just tried what you suggested but issue still same.
So then I 1) did the uncheck 2)sudo rm -rf /var/lib/apt/lists/* 3)sudo apt-get clean 4)sudo adp-get autoclean 5)sudo apr-get update

so now seems to have run past the last error but new one has cropped up.  Do you have any suggestion please?

Thanks for your help!



```
Get:40 http://archive.ubuntu.com trusty-security/universe Translation-en [72.1 kB]
Get:41 http://archive.ubuntu.com trusty Release [58.5 kB]                      
Ign http://archive.ubuntu.com trusty Release                                   
Get:42 http://archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]         
Get:43 http://archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB]    
Get:44 http://archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]     
Get:45 http://archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]     
Get:46 http://archive.ubuntu.com trusty/main i386 Packages [1,348 kB]          
Get:47 http://archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]     
Get:48 http://archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]      
Get:49 http://archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]      
Get:50 http://archive.ubuntu.com trusty/main Translation-en [762 kB]           
Get:51 http://archive.ubuntu.com trusty/multiverse Translation-en [102 kB]     
Get:52 http://archive.ubuntu.com trusty/restricted Translation-en [3,457 B]    
Get:53 http://archive.ubuntu.com trusty/universe Translation-en [4,089 kB]     
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 24.1 MB in 53s (454 kB/s)                                              
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

---

### Post by v3.xx on 2016-02-12
Manually add key (16126D3A3E5C1192) and update.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```

---

### Post by zanog.b on 2016-02-13
Hi [v3.xx]("http://ubuntuforums.org/member.php?u=1937239"),

Good Morning!

Thank you again for your valuable assistance!  Tried your suggestion, and it just worked!  Hopes no more of these errors turn up. Have a nice day.:D

Thanks & regards!

---

### Post by v3.xx on 2016-02-13
And welcome to the forum :D

---

