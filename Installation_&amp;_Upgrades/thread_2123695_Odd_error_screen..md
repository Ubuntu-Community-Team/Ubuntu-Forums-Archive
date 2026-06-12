---
title: "Odd error screen."
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by Boosh007 on 2013-03-08
For the last six or seven months, I've been receiving an error screen whenever it's time to download or update my system. It always comes up with a, "Close" box attach. It didn't really bother me until now. It's currently preventing me from upgrading my system to both Ubuntu 12 from 10 and getting the Netflix fix. It's apparently interrupting downloads of certain files and programs at random. The message reads;

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/licid/partner](http://archive.canonical.com/ubuntu/licid/partner) Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)

What would be the easiest way to fix this?...

---

### Post by Cheesemill on 2013-03-08
Can you post the output of...
```
cat -n /etc/apt/sources.list
```
There is a duplicate line in that file that needs deleting. Once we know which one I can give you the steps needed to fix it.

---

### Post by Boosh007 on 2013-03-08
1    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     2    # newer versions of the distribution.
     3    
     4    
     5    ## Major bug fix updates produced after the final release of the
     6    ## distribution.
     7    
     8    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
     9    ## team. Also, please note that software in universe WILL NOT receive any
    10    ## review or updates from the Ubuntu security team.
    11    
    12    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    13    ## team, and may not be under a free licence. Please satisfy yourself as to 
    14    ## your rights to use the software. Also, please note that software in 
    15    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    16    ## security team.
    17    
    18    ## Uncomment the following two lines to add software from the 'backports'
    19    ## repository.
    20    ## N.B. software from this repository may not have been tested as
    21    ## extensively as that contained in the main release, although it includes
    22    ## newer versions of some applications which may provide useful features.
    23    ## Also, please note that software in backports WILL NOT receive any review
    24    ## or updates from the Ubuntu security team.
    25    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
    26    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
    27    
    28    ## Uncomment the following two lines to add software from Canonical's
    29    ## 'partner' repository.
    30    ## This software is not part of Ubuntu, but is offered by Canonical and the
    31    ## respective vendors as a service to Ubuntu users.
    32    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
    33    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
    34    
    35    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse
    36    deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main multiverse restricted
    37    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe main multiverse restricted
    38    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-proposed universe main multiverse restricted
    39    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports universe main multiverse restricted

---

### Post by ibjsb4 on 2013-03-08
For some reason you have karmic in your lucid sources list.  Comment out (##) those four karmic sources and update.

To edit your sources.list:

```
gksudo gedit /etc/apt/sources.list
```

To update:

```
sudo apt-get update
```

Your update should come back error free.  If not, please post any errors.

---

### Post by Boosh007 on 2013-03-08
okay...now I get:

E: Type '1' is not known on line 1 in source list /etc/apt/sources.list
E: Type 'n' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list

---

### Post by ibjsb4 on 2013-03-08
Please post/repost the output of:

```
cat /etc/apt/sources.list.d/*
```

```
cat /etc/apt/sources.list
```

---

### Post by Boosh007 on 2013-03-08
cat /etc/apt/sources.list.d/*
deb [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) lucid main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main
# channel for the karmic (9.10) partner channel
# 
#:description:This channel contains the partner software for karmic
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# channel for the karmic (9.10) partner channel
# 
#:description:This channel contains the partner software for karmic
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# channel for the karmic (9.10) partner channel
# 
#:description:This channel contains the partner software for karmic
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
# deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) lucid main #SMPlayer
deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) lucid main #SMPlayer
deb [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) lucid main #Adobe Flash (x86-64)
deb [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) lucid main #Adobe Flash (x86-64)
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free #Swiftfox
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free #Swiftfox
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) lucid main #Ubuntu Tweak Stable Source
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) lucid main #Ubuntu Tweak Stable Source
n
deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) lucid main

AND

cat /etc/apt/sources.list
1 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
2 # newer versions of the distribution.
3
4
5 ## Major bug fix updates produced after the final release of the
6 ## distribution.
7
8 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
9 ## team. Also, please note that software in universe WILL NOT receive any
10 ## review or updates from the Ubuntu security team.
11
12 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
13 ## team, and may not be under a free licence. Please satisfy yourself as to
14 ## your rights to use the software. Also, please note that software in
15 ## multiverse WILL NOT receive any review or updates from the Ubuntu
16 ## security team.
17
18 ## Uncomment the following two lines to add software from the 'backports'
19 ## repository.
20 ## N.B. software from this repository may not have been tested as
21 ## extensively as that contained in the main release, although it includes
22 ## newer versions of some applications which may provide useful features.
23 ## Also, please note that software in backports WILL NOT receive any review
24 ## or updates from the Ubuntu security team.
25 ##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
26 ##deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
27
28 ## Uncomment the following two lines to add software from Canonical's
29 ## 'partner' repository.
30 ## This software is not part of Ubuntu, but is offered by Canonical and the
31 ## respective vendors as a service to Ubuntu users.
32 ##deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
33 ##deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
34
35 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse
36 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main multiverse restricted
37 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe main multiverse restricted
38 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-proposed universe main multiverse restricted
39 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports universe main multiverse restricted

---

### Post by ibjsb4 on 2013-03-09
Ok, lets get your PPAs out of the picture

```
sudo mv /etc/apt/sources.list.d /etc/apt/sources.list.d.old
```

```
sudo apt-get update
```

Any errors?

---

### Post by Boosh007 on 2013-03-09
sudo apt-get update
E: Type '1' is not known on line 1 in source list /etc/apt/sources.list

---

### Post by Boosh007 on 2013-03-09
I think I may have fixed it. I took out the number "1" on line one and re-ran the update. I got a message similar to the first but it said Type "2" was the problem. So I removed the number two and so forth. When I got down to line 5 I just deleted all the numbered lines from the list. I think it updated, because the system is telling that I have some 39 things to update now, where before I could only get an excuse why I couldn't do anything before. 

 sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [143kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [474kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                 
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [58.3kB]               
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release [58.3kB]                
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,357B]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,867B]  
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports Release [57.3kB]              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages    
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [291kB]   
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [668kB]           
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [4,630B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/universe Packages [7,125B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/main Packages [124kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/multiverse Packages [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/restricted Packages [14B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/universe Packages [56.1kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/main Packages [19.0kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/multiverse Packages [1,378B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/restricted Packages [14B]
Fetched 2,040kB in 2s (852kB/s)                      
Reading package lists... Done

---

### Post by ibjsb4 on 2013-03-09
Ok, look like your ready to upgrade.  Good luck :)

---

### Post by Boosh007 on 2013-03-09
Thanks, next I'll attack the Netflix problem...Nah...Maybe another day...lol

---

