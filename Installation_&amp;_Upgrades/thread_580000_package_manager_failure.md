---
title: "package manager failure"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by ggumas on 2007-10-18
I recently loaded ubuntu feisty on my laptop, using an alternate CD.
Now when I try to add packages I get a hang up in that  I am asked to insert a Feisty Fawn disc in my cd drive. When  I do so it is not recognized and I am unable to load the package. 

A typical session is as follows:
>    Using the synaptic package manager , I request the loading of   adept-manager.
 >I receive a response of tghe sort
     "Apply the following changes?
     adept-common (version 2.1.2ubuntu26.1) will be installed
     adept-manager (version 2.1.2ubuntu26.1) will be installed
     kdelibs4c2a (version 4:3.5.6-0ubuntu14.1) will be installed
     konsole (version 4:3.5.6-0ubuntu20.7) will be installed
    libpcre3 (version 6.7-1ubuntu2) will be installed"
 
>   I then click ok.
    and I am prompted with the message:
         "Please insert the disk labeled
          Ubumtu 7.04_FeistyFawn_-Release i386(2007415)
         in drive /cdrom/"
>I insert the disc, but ubuntu fails to recognize it
   >After which I get the following message
    "W: Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386    
    (20070415)]/pool/main/p/pcre3/libpcre3_6.7-1ubuntu2_i386.deb"


Can someone out there  give  me a clue as to what is going on?


George

---

### Post by mattpker on 2007-10-18
Try running:

sudo apt-get install adept-manager

This will install adept-manager from the repositories and not your cd.

---

### Post by ggumas on 2007-10-18
Thanks for the suggestion but it failed to solve my problem
as indicated by the following session

george@ggubuntu:~$ sudo apt-get install adept-manager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adept-common kdelibs4c2a konsole libpcre3
Suggested packages:
  fam khelpcenter
Recommended packages:
  libqt-perl perl-suid
The following NEW packages will be installed:
  adept-common adept-manager kdelibs4c2a konsole libpcre3
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.8MB of archives.
After unpacking 34.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter

>> I did so and received
Media change: please insert the disc labeled
 'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter

George

---

### Post by ggumas on 2007-10-19
Re Package manager failure:
       I finally discovered my problem. For some reason the ubuntu Repositories were'nt set up properly. After I went to Synaptic Package manager and reconfigured the Repositories, my problem disappeared
George

---

### Post by changuito on 2007-11-15
Hey! I'm glad your problems were solved and thanks for giving a glimer of what you did. Could you give a bit more details. I'm struggling with some crazy things I'm seeing in adept, and i suspect it's related to your issue. 
thanks a million.

---

### Post by changuito on 2007-11-25
I read somewhere else that if you are NOT connected to the internet when yo uinstall gutsy, then you will have repository source issues. there is a way to fix this after install by uncommenting lines in some file (sorry, i cant find the details anymore). This didnt work well for me, so i reinstalled while connected to the internet, and that solved my problems. You'd think that gutsy would suggest connecting to the internet when performing and install....

---

### Post by Teknyk on 2007-11-27
> **changuito said:**
> Hey! I'm glad your problems were solved and thanks for giving a glimer of what you did. Could you give a bit more details. I'm struggling with some crazy things I'm seeing in adept, and i suspect it's related to your issue. 
thanks a million.

Not sure what you are dealing with but I was just trying to install alien from the CLI and would get the same thing "Media change: please insert the disc labeled" asking me to insert the ubuntu cd.

apt-get update would do something similar and mention the CD as well.

```
*********@beast:~$ sudo apt-get update 
[sudo] password for **********:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                  
Get:2 http://archive.canonical.com gutsy Release.gpg [191B]                 
Ign http://archive.canonical.com gutsy/partner Translation-en_US
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US
Hit http://archive.ubuntu.com gutsy Release    
Hit http://archive.canonical.com gutsy Release 
Hit http://archive.ubuntu.com gutsy/main Packages
Ign http://archive.canonical.com gutsy/partner Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Ign http://archive.canonical.com gutsy/partner Sources
Hit http://archive.canonical.com gutsy/partner Packages
Hit http://archive.canonical.com gutsy/partner Sources
Fetched 2B in 1s (2B/s)
Reading package lists... Done
**********@beast:~$
```

In my software sources, Ubuntu Software tab, at the bottom was "Installable from CD-ROM/DVD"

I unchecked that box and the no more cd rom crap at the CLI.

Now if this was a good idea or not... I couldn't say. I am still too new to this.
I can say I got alien installed just fine after that though :)

---

