---
title: "Need help with a lot"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by SamFromSpace on 2008-03-09
Ok, Just installed ubuntu 7:10 on my ps3, and have no idea how to download the "Neccessities" Such as java sun, flash and to a lesser extent limewire. Belive me when i say i'm the worlds biggest ubuntu noob. (I only found out ubuntu existed about 2 weeks ago) and have never used l;inux before. Any help that doesn't require any technological knowledge is much appreciated :)

---

### Post by taurus on 2008-03-09
Go into System -> Administration -> Synaptic Package Manager and Search for whatever you want to install.  Click the package you want and install it from there.  Otherwise, you can install it from a terminal (make sure you don't have synaptic open first) with

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin flashplugin-nonfree frostwire
```

---

### Post by SamFromSpace on 2008-03-09
I get this message back: 





```
samfromspace@PS3:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin flashplugin-nonfree frostwire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sun-java6-jre
E: Package sun-java6-bin has no installation candidate

```

Any idea?

---

### Post by taurus on 2008-03-09
Looks like you don't have any or limited number of repos enable in /etc/apt/sources.list.  Therefore, you need to enable them before you can install anything.

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line to comment out the cdrom.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down the gedit editing window.

Now run

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by SamFromSpace on 2008-03-09
Well i got a different error message, progress i guess

```
samfromspace@PS3:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
E: Type 'Line' is not known on line 5 in source list /etc/apt/sources.list
E: The list of sources could not be read.

```

---

### Post by taurus on 2008-03-09
There is something wrong with line 5 in your /etc/apt/sources.list.  So, can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by SamFromSpace on 2008-03-09
Yep. The whole thing.... 


```
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release powerpc+ps3 (20071016)]/ gutsy main
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

Line commented out by installer because it failed to verify:
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy main restricted
Line commented out by installer because it failed to verify:
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
 Line commented out by installer because it failed to verify:
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates main restricted
 Line commented out by installer because it failed to verify:
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 Line commented out by installer because it failed to verify:
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy universe
 Line commented out by installer because it failed to verify:
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy universe
 Line commented out by installer because it failed to verify:
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates universe
 Line commented out by installer because it failed to verify:
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
 Line commented out by installer because it failed to verify:
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy multiverse
 Line commented out by installer because it failed to verify:
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy multiverse
 Line commented out by installer because it failed to verify:
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates multiverse
 Line commented out by installer because it failed to verify:
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
 or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-backports main restricted universe multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
 users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

 Line commented out by installer because it failed to verify:
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-security main
 Line commented out by installer because it failed to verify:
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-security main
 Line commented out by installer because it failed to verify:
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-security universe
 Line commented out by installer because it failed to verify:
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-security universe
 Line commented out by installer because it failed to verify:
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-security multiverse
 Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy universe multiverse main
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-security multiverse

```

---

### Post by Ptero-4 on 2008-03-09
Check your sources.list file (specifically the 5th line in it) there is a sintax error in there.
Also flash is not available for the powerpc architecture (which the playstation 3 is based on). You'll need to install gnash for the flash content.

P.S: Comment every line that doesn't begin with deb, deb-src and the "cdrom" line.

---

### Post by SamFromSpace on 2008-03-09
In front of these?

```
Line commented out by installer because it failed to verify:
```

---

### Post by taurus on 2008-03-09
If you read my #4, it said to only remove # in front of lines that start with **[COLOR="Blue"]deb[/COLOR]** & **[COLOR="Blue"]deb-src[/COLOR]**!  Therefore, you need to put the # back in front of all the lines that don't start with deb & deb-src.

---

### Post by .nedberg on 2008-03-09
> **SamFromSpace said:**
> In front of these?

```
Line commented out by installer because it failed to verify:
```

Yes, place a # in front of those!

---

### Post by SamFromSpace on 2008-03-09
Ok, i changed it again, and now i get one huge error message....

[Spoiler]
```
samfromspace@PS3:~$ sudo apt-get update
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Get:2 http://archive.canonical.com gutsy Release.gpg [191B]         
Ign http://archive.canonical.com gutsy/partner Translation-en_US    
Hit http://security.ubuntu.com gutsy-security Release               
Hit http://archive.canonical.com gutsy Release                      
Hit http://security.ubuntu.com gutsy-security/universe Packages     
Hit http://archive.canonical.com gutsy/partner Packages             
Hit http://security.ubuntu.com gutsy-security/main Packages         
Hit http://security.ubuntu.com gutsy-security/multiverse Packages   
Hit http://archive.canonical.com gutsy/partner Sources              
Get:3 http://ports.ubuntu.com gutsy Release.gpg [191B]              
Ign http://ports.ubuntu.com gutsy/main Translation-en_US           
Ign http://ports.ubuntu.com gutsy/restricted Translation-en_US
Ign http://ports.ubuntu.com gutsy/universe Translation-en_US
Ign http://ports.ubuntu.com gutsy/multiverse Translation-en_US
Get:4 http://ports.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://ports.ubuntu.com gutsy-updates/main Translation-en_US    
Ign http://ports.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://ports.ubuntu.com gutsy-updates/multiverse Translation-en_US
Get:5 http://ports.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://ports.ubuntu.com gutsy-backports/main Translation-en_US
Get:6 http://ports.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://ports.ubuntu.com gutsy-security/main Translation-en_US
Ign http://ports.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://ports.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://ports.ubuntu.com gutsy Release                   
Hit http://ports.ubuntu.com gutsy-updates Release           
Hit http://ports.ubuntu.com gutsy-backports Release                 
Hit http://ports.ubuntu.com gutsy-security Release                  
Hit http://ports.ubuntu.com gutsy/main Packages                     
Hit http://ports.ubuntu.com gutsy/restricted Packages               
Ign http://ports.ubuntu.com gutsy/main Sources              
Ign http://ports.ubuntu.com gutsy/restricted Sources
Hit http://ports.ubuntu.com gutsy/universe Packages         
Ign http://ports.ubuntu.com gutsy/universe Sources          
Hit http://ports.ubuntu.com gutsy/multiverse Packages
Ign http://ports.ubuntu.com gutsy/multiverse Sources
Hit http://ports.ubuntu.com gutsy-updates/main Packages
Ign http://ports.ubuntu.com gutsy-updates/main Sources      
Hit http://ports.ubuntu.com gutsy-updates/universe Packages 
Ign http://ports.ubuntu.com gutsy-updates/universe Sources  
Hit http://ports.ubuntu.com gutsy-updates/multiverse Packages
Ign http://ports.ubuntu.com gutsy-updates/multiverse Sources
Hit http://ports.ubuntu.com gutsy-backports/main Packages   
Ign http://ports.ubuntu.com gutsy-backports/main Sources    
Hit http://ports.ubuntu.com gutsy-security/main Packages
Ign http://ports.ubuntu.com gutsy-security/main Sources     
Hit http://ports.ubuntu.com gutsy-security/universe Packages
Ign http://ports.ubuntu.com gutsy-security/universe Sources
Hit http://ports.ubuntu.com gutsy-security/multiverse Packages
Ign http://ports.ubuntu.com gutsy-security/multiverse Sources
Err http://ports.ubuntu.com gutsy/main Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy/restricted Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy/universe Sources          
  404 Not Found
Err http://ports.ubuntu.com gutsy/multiverse Sources        
  404 Not Found
Err http://ports.ubuntu.com gutsy-updates/main Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-updates/universe Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-updates/multiverse Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-backports/main Sources    
  404 Not Found
Err http://ports.ubuntu.com gutsy-security/main Sources     
  404 Not Found
Err http://ports.ubuntu.com gutsy-security/universe Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-security/multiverse Sources
  404 Not Found
Get:7 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US
Ign http://archive.ubuntu.com gutsy/main Translation-en_US
Get:8 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_US
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
Get:9 http://archive.ubuntu.com gutsy-proposed Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-proposed/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-proposed/main Translation-en_US
Ign http://archive.ubuntu.com gutsy-proposed/multiverse Translation-en_US
Get:10 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com gutsy Release
Hit http://archive.ubuntu.com gutsy-backports Release
Hit http://archive.ubuntu.com gutsy-proposed Release
Hit http://archive.ubuntu.com gutsy-updates Release
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy-backports/universe Packages
Hit http://archive.ubuntu.com gutsy-backports/main Packages
Hit http://archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://archive.ubuntu.com gutsy-proposed/universe Packages
Hit http://archive.ubuntu.com gutsy-proposed/main Packages
Hit http://archive.ubuntu.com gutsy-proposed/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Fetched 10B in 5s (2B/s)
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/main/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/universe/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/main/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/universe/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-backports/main/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/multiverse/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
samfromspace@PS3:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin

``` [/SPOILER]

---

### Post by .nedberg on 2008-03-09
Try to replace every line that starts with:
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
and replace it with
deb [http://ports.ubuntu.com/ubuntu-ports/dists/](http://ports.ubuntu.com/ubuntu-ports/dists/)

(or just add dists/ at the end)

then do a sudo apt-get update again

I would recommend you backup your sources.list...

---

### Post by taurus on 2008-03-09
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and change the server to Main Server.  Save it and shut down synaptic and run this command again and post the output here.

```
sudo apt-get update
```

---

### Post by SamFromSpace on 2008-03-09
Tried them both, and it came back with an identical message as it did before

---

### Post by Civo on 2008-06-05
Hi sam, 

Been around PS3 Ubuntu for a while... I have Feisty 7.04 installed in my PS3 and the internet is really a pain.

For what I've managed to do and find out until now, Java and Flash will have litlle ou no support on the PS3.

For Flash you need to install another application, a plugin called gnash (someone correct me if I'm wrong, please), and even so, not all contents will be playable thru that plugin.

When it comes to Java, I'm only able to use the default version of Feisty, that allows to view a very little number of Java contents.

So I think until someone comes up with an alternative way to install both this features, we're stuck to "normal" web pages.


Good luck, and  despite all that, don't give up on Ubuntu!

---

