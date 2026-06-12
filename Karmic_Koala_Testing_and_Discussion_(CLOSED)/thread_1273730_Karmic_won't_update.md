---
title: "Karmic won't update"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-09-23
Hey, has karmic had ANY updates since alpha 6 'cause if it has I'm not getting them. I get this error.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 57B0CE6D09827771

Anyone know how to fix this?

---

### Post by ranch hand on 2009-09-23
Surely this is not the only repo that you are using.  That error should not stop you from getting updates.

Just how are you trying to get these updates?

Have you tried going to the terminal and runing;
```

sudo apt-get update

```
and then;
```

sudo apt-get upgrade

```
?

---

### Post by Sashin on 2009-09-23
Here is the output:

```
ubuntu@PC:~$ sudo apt-get update
[sudo] password for ubuntu: 
Hit http://au.archive.ubuntu.com karmic Release.gpg
Ign http://au.archive.ubuntu.com karmic/main Translation-en_AU                 
Ign http://au.archive.ubuntu.com karmic/restricted Translation-en_AU           
Ign http://au.archive.ubuntu.com karmic/universe Translation-en_AU             
Ign http://au.archive.ubuntu.com karmic/multiverse Translation-en_AU           
Hit http://au.archive.ubuntu.com karmic-updates Release.gpg          
Hit http://archive.canonical.com karmic Release.gpg                  
Ign http://archive.canonical.com karmic/partner Translation-en_AU    
Get:1 http://ppa.launchpad.net karmic Release.gpg [307B]             
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_AU          
Ign http://ppa.launchpad.net karmic/main Translation-en_AU                     
Ign http://au.archive.ubuntu.com karmic-updates/main Translation-en_AU         
Ign http://au.archive.ubuntu.com karmic-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com karmic-updates/universe Translation-en_AU
Hit http://archive.canonical.com karmic Release                      
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_AU    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_AU      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_AU    
Ign http://au.archive.ubuntu.com karmic-updates/multiverse Translation-en_AU   
Hit http://security.ubuntu.com karmic-security Release                         
Get:2 http://ppa.launchpad.net karmic Release [66.0kB]                         
Ign http://ppa.launchpad.net karmic Release                                    
Hit http://au.archive.ubuntu.com karmic-proposed Release.gpg                   
Ign http://au.archive.ubuntu.com karmic-proposed/restricted Translation-en_AU  
Ign http://au.archive.ubuntu.com karmic-proposed/main Translation-en_AU        
Ign http://archive.canonical.com karmic/partner Packages                       
Ign http://au.archive.ubuntu.com karmic-proposed/multiverse Translation-en_AU  
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://ppa.launchpad.net karmic/main Packages                              
Ign http://au.archive.ubuntu.com karmic-proposed/universe Translation-en_AU    
Hit http://au.archive.ubuntu.com karmic Release                                
Hit http://au.archive.ubuntu.com karmic-updates Release                        
Ign http://archive.canonical.com karmic/partner Sources                        
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://au.archive.ubuntu.com karmic-proposed Release                       
Hit http://ppa.launchpad.net karmic/main Sources                               
Hit http://au.archive.ubuntu.com karmic/main Packages                          
Hit http://au.archive.ubuntu.com karmic/restricted Packages                    
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://au.archive.ubuntu.com karmic/main Sources                           
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://au.archive.ubuntu.com karmic/restricted Sources                     
Hit http://au.archive.ubuntu.com karmic/universe Packages                      
Hit http://archive.canonical.com karmic/partner Sources                        
Hit http://au.archive.ubuntu.com karmic/universe Sources                       
Hit http://au.archive.ubuntu.com karmic/multiverse Packages
Hit http://au.archive.ubuntu.com karmic/multiverse Sources 
Hit http://au.archive.ubuntu.com karmic-updates/main Packages
Hit http://au.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://au.archive.ubuntu.com karmic-updates/main Sources
Hit http://au.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://au.archive.ubuntu.com karmic-updates/universe Packages
Hit http://au.archive.ubuntu.com karmic-updates/universe Sources
Hit http://au.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://au.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://au.archive.ubuntu.com karmic-proposed/restricted Packages
Hit http://au.archive.ubuntu.com karmic-proposed/main Packages
Hit http://au.archive.ubuntu.com karmic-proposed/multiverse Packages
Hit http://au.archive.ubuntu.com karmic-proposed/universe Packages
Fetched 308B in 4s (72B/s)                                 
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 57B0CE6D09827771
W: You may want to run apt-get update to correct these problems
ubuntu@PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@PC:~$ 

```

---

### Post by jarede on 2009-09-23
It looks like you just need to import the key for the ppa:

```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 57B0CE6D09827771

```

Should see the a message saying the key was imported and doing update again should show no GPG error

---

### Post by kansasnoob on 2009-09-23
It might be helpful to see your sources.list:

```
cat /etc/apt/sources.list
```

---

### Post by Sashin on 2009-09-23
okay now I don't get any errors or updates either.

> [B]# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Alpha amd64 (20090917.1)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

deb [http://ppa.launchpad.net/ubuntu-boot/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-boot/ppa/ubuntu) karmic main
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://ppa.launchpad.net/ubuntu-boot/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-boot/ppa/ubuntu) karmic main
[/B]

---

### Post by ranch hand on 2009-09-23
Man, all that looks cool.

What do you get with;
```

uname -a

```
That will give your active kernal and give us an idea how far out you are on updates.

This is nuts, I am on a new A6 install that I just updated and added medibuntu and got my tunes going.  Piece of cake.

There is something here that does not make a lot of sense.

---

### Post by ranch hand on 2009-09-23
Is this a clean install or an update from 9.04?

---

### Post by Sashin on 2009-09-23
Its a clean install. If there have been any updates from alpha 6 I haven't got them.

---

### Post by ranch hand on 2009-09-23
When did you install it?  That is what I wanted the "uname -a" data for.

---

### Post by rykel on 2009-09-23
Hi pals,

I have a somewhat similar situation... my Karmic would not AUTO-update, but it can be done manually via "sudo apt-get update/upgrade".

Just curious if this non-auto-update is a feature or bug?

My "uname -a" is ***"Linux SuperStar 2.6.31-10-generic #34-Ubuntu SMP Wed Sep 16 00:23:19 UTC 2009 i686 GNU/Linux"***

---

### Post by kansasnoob on 2009-09-23
It might be worth going to Software Sources and trying the "Main Server".

---

### Post by kansasnoob on 2009-09-23
> **rykel said:**
> Hi pals,

I have a somewhat similar situation... my Karmic would not AUTO-update, but it can be done manually via "sudo apt-get update/upgrade".

Just curious if this non-auto-update is a feature or bug?

My "uname -a" is ***"Linux SuperStar 2.6.31-10-generic #34-Ubuntu SMP Wed Sep 16 00:23:19 UTC 2009 i686 GNU/Linux"***

Can't really say, I've also been updating mostly using the command line.

---

### Post by VMC on 2009-09-23
> **Sashin said:**
> okay now I don't get any errors or updates either.
Maybe you updated. Have you tried "sudo apt-get clean" or "sudo apt-get purge" ?

---

### Post by ranch hand on 2009-09-23
That sounds like a bug to me.

What I would like to know is where did you get this SuperStar deal.  I don't get that on mine.  I am on 2.6.31-10.35.

I don't use the update manager at all, never have liked it.  I started on dialup and it is a pain in the butt.  I either use apt or synaptic where you can choose what to download at one time.  When it takes an hour for each Mb you have to do it in pieces.  Update manager always selects all the buggers and you have to undo the stuff.  A lot easier just to select the ones you want.

As far as your problem goes, I would report it.  There is probably a bug report on it and you can just click on "effects me too".   It will, I am sure, get straightened out.

---

### Post by ranch hand on 2009-09-23
> **VMC said:**
> Maybe you updated. Have you tried "sudo apt-get clean" or "sudo apt-get purge" ?
Or "sudo dpkg --configure -a"

---

### Post by rykel on 2009-09-24
> **ranch hand said:**
> 
What I would like to know is where did you get this SuperStar deal.  I don't get that on mine.  I am on 2.6.31-10.35.


sorry that "SuperStar" is the name of my laptop.  :lolflag:

I will wait and see if it still persists..

btw, on a sidetrack, is any of you on Karmic stuck on Firefox 3.5.2? My unit was upgraded online from Jaunty, and I have another PC with a fresh install Karmic that is already running 3.5.3.

---

### Post by d_eckert on 2009-09-24
> **kansasnoob said:**
> It might be worth going to Software Sources and trying the "Main Server".

This is what I had to do to get updates on my system.
When using the AU mirror I got nothing, changed to the main server and had 400+ updates

---

### Post by ranch hand on 2009-09-24
By cracky, that may be the deal.  I have never had trouble with any of the repos I have tried but the  au repo is not one I have tried.  Seemed kind of a long way from here.

But them thar intertubes go all over.

---

### Post by nhasian on 2009-09-24
update-manager stopped updating for me to today.  I dont know if you noticed or not, but it doesnt ask you for your super user password, which is probably why it cant update.

sudo apt-get upgrade from a command line worked fine though

---

### Post by celticbhoy on 2009-09-24
> **nhasian said:**
> update-manager stopped updating for me to today.  I dont know if you noticed or not, but it doesnt ask you for your super user password, which is probably why it cant update.

sudo apt-get upgrade from a command line worked fine though

Update-manager has been updated and works a little differently now, it only asks for password when you install, not to check.

---

