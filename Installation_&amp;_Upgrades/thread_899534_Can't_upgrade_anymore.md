---
title: "Can't upgrade anymore"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by andyvito on 2008-08-24
Hi, since I messed up a little my source list a couple of weeks ago, the upgrade manager doesn't show me any upgrade to do. I try with apt-get upgrade but it doesn't upgrade anything, and it dosn't give me any error.
It looks strange to me as usually every second day or so there were some upgrades available.
How can I check if something is wrong?
Thanks in advance, Andy

---

### Post by Sam Lars on 2008-08-24
It sounds like it's working, but could you post your /etc/apt/sources.list?
You can also compare it to the one [here]("http://ubuntuforums.org/showpost.php?p=4214207&postcount=2") (replace "gutsy" with "hardy" of course).

---

### Post by andyvito on 2008-08-24
Hi sam, here the content of that file

> # deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

Do you think there's something wrong?
Maybe upgrades have been "freezed" for the release of Ubuntu 8.10?
I don't think so... anyway, let me know if you can. Thanks a lot.

---

### Post by Sam Lars on 2008-08-24
It looks fine to me.  You'll still get updates for Hardy for at least a couple years, since it's an LTS.  Once Intrepid is released, it may be less.
Sometimes there's just a lull in updates.  You could try
```
sudo apt-get update
```
to make sure it's updating the package information correctly.

---

### Post by andyvito on 2008-08-24
Thanks a lot Sam, I'll try tomorrow morning and I'll tell you about.
Thanks again

---

### Post by andyvito on 2008-08-25
Hi Sam, it's morning now here in Italy...
That's what apt-get update gives me:

```
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-it              
Ign http://security.ubuntu.com hardy-security/restricted Translation-it        
Ign http://security.ubuntu.com hardy-security/universe Translation-it          
Ign http://security.ubuntu.com hardy-security/multiverse Translation-it        
Hit http://it.archive.ubuntu.com hardy Release.gpg                             
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://it.archive.ubuntu.com hardy/main Translation-it                     
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://it.archive.ubuntu.com hardy/restricted Translation-it               
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://it.archive.ubuntu.com hardy/universe Translation-it                 
Hit http://it.archive.ubuntu.com hardy/multiverse Translation-it   
Hit http://it.archive.ubuntu.com hardy-updates Release.gpg         
Ign http://it.archive.ubuntu.com hardy-updates/main Translation-it 
Ign http://it.archive.ubuntu.com hardy-updates/restricted Translation-it
Ign http://it.archive.ubuntu.com hardy-updates/universe Translation-it
Ign http://it.archive.ubuntu.com hardy-updates/multiverse Translation-it
Hit http://it.archive.ubuntu.com hardy Release                     
Hit http://it.archive.ubuntu.com hardy-updates Release                         
Hit http://it.archive.ubuntu.com hardy/main Packages                           
Hit http://it.archive.ubuntu.com hardy/restricted Packages         
Hit http://it.archive.ubuntu.com hardy/main Sources                
Hit http://it.archive.ubuntu.com hardy/restricted Sources          
Hit http://it.archive.ubuntu.com hardy/universe Packages           
Hit http://it.archive.ubuntu.com hardy/universe Sources            
Hit http://it.archive.ubuntu.com hardy/multiverse Packages         
Hit http://it.archive.ubuntu.com hardy/multiverse Sources          
Hit http://it.archive.ubuntu.com hardy-updates/main Packages       
Hit http://it.archive.ubuntu.com hardy-updates/restricted Packages 
Hit http://it.archive.ubuntu.com hardy-updates/main Sources        
Hit http://it.archive.ubuntu.com hardy-updates/restricted Sources  
Hit http://it.archive.ubuntu.com hardy-updates/universe Packages   
Hit http://it.archive.ubuntu.com hardy-updates/universe Sources    
Hit http://it.archive.ubuntu.com hardy-updates/multiverse Packages 
Hit http://it.archive.ubuntu.com hardy-updates/multiverse Sources  
Lettura della lista dei pacchetti in corso... Fatto  (Means: Reading packages list... Done)

```

The problem came since when I tryied to add a Medibuntu repository to download some codecs for ffmpeg. I added some lines to the list whit a command I found in this forum, but as that repository seemed to be always down I removed them. Maybe I removed something else too...
I'll try to find that command again and I'll post here to you to see.
Thanks again

---

### Post by andyvito on 2008-08-25
I did the same as I tryied when I messed up before, the command added Medibuntu repository to my list, and now this is the only one working!!!
the command is:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Anyway, all the rest still not working...
Switched from the italian server to the main...
Same...

Last time I erased manually all the lines regerding medibuntu because seemed to be always down...
 I don't know, sources.list seem to be ok...
Is not possible to reinstall aptitude?
Maybe you need aptitude to install aptitude...
Anyway, I'll keep on trying...
Thanks

---

### Post by Partyboi2 on 2008-08-25
I think you will find that its just a lull in the updates just like Sam Lars has mentioned.

---

### Post by andyvito on 2008-08-28
Hope so...
Thanks again

---

