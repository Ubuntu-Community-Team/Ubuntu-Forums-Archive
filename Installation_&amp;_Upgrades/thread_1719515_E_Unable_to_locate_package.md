---
title: "E: Unable to locate package"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by gatechmp3 on 2011-04-01
To start, I am a very new user of ubuntu, so please bear with me. I just installed ubuntu on an old desktop and cannot get it to install packages. I installed these same packages on my laptop that is a little newer and it works on the laptop, but it wont work on the desktop. I searched for previous threads and found to try ```
cat /etc/apt/sources.list
```which results in this, i have no idea what i am looking at though```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse restricted universe main
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse restricted universe main #Added by software-properties
```I also tried this many times and nothing has changed```
sudo apt-get update
```Please help me with this, I dont know what else to do. Thanks.

---

### Post by mörgæs on 2011-04-02
HI, welcome to the fora.

If 
```
 sudo apt-get update
```
does not yield any results, it could simply be because your system is fully updated. 

Is it also a problem with installing new applications? 

Your sources.list is fine.

---

### Post by gatechmp3 on 2011-04-02
this is the output for this
```
sudo apt-get update
``````
Hit http://us.archive.ubuntu.com maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Hit http://archive.ubuntu.com maverick Release.gpg                             
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://archive.ubuntu.com maverick Release                                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Hit http://extras.ubuntu.com maverick Release                                  
Hit http://archive.canonical.com maverick Release                              
Hit http://us.archive.ubuntu.com maverick Release                    
Hit http://archive.ubuntu.com maverick/main Sources                            
Hit http://extras.ubuntu.com maverick/main Sources                   
Hit http://archive.canonical.com maverick/partner Sources            
Hit http://us.archive.ubuntu.com maverick/multiverse Sources         
Hit http://archive.ubuntu.com maverick/restricted Sources            
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Hit http://archive.canonical.com maverick/partner i386 Packages      
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Fetched 72B in 0s (76B/s)
Reading package lists... Done

```These are new applications to this computer, however i have these same applications installed on another computer and they work fine on the other computer.

The names of the applications are etmmanager and timelogger, if that matters, i need both as they work together.

thanks.

---

### Post by Dutch70 on 2011-04-02
Everything looks fine there too. Of course you have to follow that up with ```
sudo apt-get upgrade
```

You didn't say anything about how you're trying to install them.

---

### Post by gatechmp3 on 2011-04-02
I tried running what you suggested and got this
```
sudo apt-get upgrade
``````
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```I have been trying to install using the terminal and using this
```
sudo apt-get install timelogger
``````
sudo apt-get install etmmanager
```the result of those are
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package timelogger

``````
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package etmmanager
```

thanks for all the help so far.

---

### Post by gatechmp3 on 2011-04-02
i just tried to install mysql on this computer now and this is what i got. i used this command in terminal.
```
sudo apt-get install mysql-server
```

And this was the result.
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mysql-server : Depends: mysql-server-5.1 but it is not going to be installed
E: Broken packages
```

thanks.

---

### Post by mörgæs on 2011-04-02
Try to open Software Sources and select another mirror.

---

### Post by mörgæs on 2011-04-02
Just saw the post about broken packages. Try these:

```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
```

---

### Post by gatechmp3 on 2011-04-02
I changed the mirror to the main server, and tired all the code you gave. mysql now installed, but etmmanager and timelogger are still not found.

---

### Post by gatechmp3 on 2011-04-02
I dont know if this matters or not, but when updating the software source list, a lot of the individual status bars are reading failed under the details of the update.

---

### Post by Dutch70 on 2011-04-02
> **gatechmp3 said:**
> I changed the mirror to the main server, and tired all the code you gave. mysql now installed, but etmmanager and timelogger are still not found.

You will probably have to download them first. :D

---

### Post by gatechmp3 on 2011-04-02
i have them downloaded in the downloads folder, do they need to be moved somewhere specific?

---

### Post by gatechmp3 on 2011-04-02
i got it figured out, i just had to manually install the dependencies, since they were obsolete. thanks for everyones help.

---

### Post by Dutch70 on 2011-04-02
Different types of downloads/packages need to be installed different ways, So it depends on what you downloaded.

---

### Post by gatechmp3 on 2011-04-02
thanks for all your help, it looks like we were posting at the same time. i will definetly have more questions, so ill ask when they come up

---

### Post by Dutch70 on 2011-04-03
Hey, you aren't posting right now are you? ;) j/k

Nice work! Glad to hear you got it figured out, and got them installed.

Best regards
Dutch

---

