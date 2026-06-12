---
title: "Duplicate source list entry problem"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by ngchandrasekhar on 2013-05-20
Hello
I while updating with sudo apt-get update I am getting some source list problem 
sekhar@sekhar-laptop:~$ sudo apt-get update
[sudo] password for sekhar: 
> Get:1 [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/ Release.gpg [490B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg           
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security Release.gpg
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Ign [http://ftp.iitm.ac.in/cran/bin/linux/ubuntu/](http://ftp.iitm.ac.in/cran/bin/linux/ubuntu/) lucid/ Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/main Packages            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/restricted Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/main Sources             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/restricted Sources       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/universe Packages        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/universe Sources         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/multiverse Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/multiverse Sources
Get:2 [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/ Release [2,270B]
Ign [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/ Release           
Get:3 [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/ Packages [62.7kB]                           
Fetched 65.5kB in 9s (6,618B/s)                                                
Reading package lists... Done
W: GPG error: [http://ftp.iitm.ac.in](http://ftp.iitm.ac.in) lucid/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)

I tried to check the sources. list  to find the duplicate sources. list..but could not solve the problem. but yes while running the sedu apt- get update second time its not sawing the warning.. but again the same warning is there ..I am attaching the sources. list below.

> # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb [http://ftp.iitm.ac.in/cran/bin/linux/ubuntu](http://ftp.iitm.ac.in/cran/bin/linux/ubuntu) lucid/[/QUOTE]



 Please help me solving the problem . Thank you with regards .

---

### Post by claracc on 2013-05-20
About the key error in [http://ftp.iitm.ac.in/cran/bin/linux/ubuntu](http://ftp.iitm.ac.in/cran/bin/linux/ubuntu), you have explanation in the site:

```
Announcement: Due to sever issues, the Ubuntu CRAN packages have been signed with a new pgp key. See SECURE APT below
```

So you will have to add the new key in the way addressed in the web:

 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9

---

### Post by ajgreeny on 2013-05-20
Lucid has now lost its support so you will need to update to a newer ubuntu version, I'm afraid.

Forget about the duplicate sources; you will not be able to easily update any more.  I suggest 12.04 as the best option for you, and if you don't want or like unity try Xubuntu 12.04 instead. Xubuntu has a more conventional DE and you will probably find that it is very like ubuntu Lucid in many ways.

---

### Post by fantab on 2013-05-20
+1 to ajgreeny.
Your issue is not what it says it is. Its that Lucid is dead, no more updates. You have to install 12.04.

---

### Post by ngchandrasekhar on 2013-05-22
> **fantab said:**
> +1 to ajgreeny.
Your issue is not what it says it is. Its that Lucid is dead, no more updates. You have to install 12.04.

thank you.. Does it mean no  more ubuntu 10.04.?:confused:

---

### Post by ngchandrasekhar on 2013-05-22
thank you all .. But I still want to know if there is any other alternative solution rather upgrading to 12.04. Please help me thank you..Thank you again

---

### Post by fantab on 2013-05-22
> **ngchandrasekhar said:**
> thank you all .. But I still want to know if there is any other alternative solution rather upgrading to 12.04. Please help me thank you..Thank you again

Why do you want an "alternative solution rather upgrading to 12.04"? With all support for 10.04 has stopped there is no alterantive but to upgrade. Is there any special reason why you don't want to upgrade?

---

### Post by claracc on 2013-05-23
You can find more information in this link: [http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support](http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support)

Doing what this link indicates you can install software through synaptic or software center but you won't receive any update.

---

### Post by p-dh on 2013-05-23
Another solution is to try [Y-PPA Manager]("https://launchpad.net/~webupd8team/+archive/y-ppa-manager?field.series_filter=lucid") and let it fix the issue. 10.04 desktop has been sunsetted - 10.04 server still has two years. So, certain archives are and will be still available.
A quick addition is that I have updated all my 10.04 PCs to 12.04 - including a vastly underpowered netbook. They all run 12.04 at least as well as 10.04 with the added advantage of having desktop support through 2017.

Peace,
Paul :cool:

---

### Post by ngchandrasekhar on 2013-05-23
Thank you all for all the suggestion. The reason of retaining 10.04 was only because once I tried to upgrade to 11. 04 but it didnt goes well.. Now  I have upgraded to 12.04. Thanks to all your suggestion..  but I have a small query. I found the upgrade versiono to be 32bit. As my processor is 64 bit. I want to know whether its alright or shall I download the 64 bit.  Help me to know the differences between the two.  Thank you again.

---

### Post by fantab on 2013-05-23
If your processor is 64bit then install 64bit Ubuntu, it will perform better than 32bit. 32bit is old technology while 64bit is newer.

---

### Post by ubu_dynamite on 2013-05-23
32bit will work just fine to 64bit consumes more ram so if your low on that stick with 32bit.

---

### Post by p-dh on 2013-05-23
If you had 32-bit 10.04 and did an in-place upgrade, you would receive the 32-bit 12.04. You cannot simply upgrade from 32-bit to 64-bit, you must do a reinstall. 
For more info on the difference between 32-bit and 64-bit, [here]("https://help.ubuntu.com/community/32bit_and_64bit") is a good place to start. The original issues associated with running 64-bit have disappeared (I simply haven't seen any) and it's worth considering if you are doing a new install or setting up a new PC.

Peace,
Paul :cool:

---

