---
title: "problem upgrade from feisty to gutsy!"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by ne0hit on 2007-10-24
hello everybody! 
my english isn't perfect, i'm italian ubuntu user, and i don't find help in the italian forum.
i want to upgrade to gutsy, i push alt+F2 and i write in gksu "update-manager-c"

it give me this error: ""Failed to fetch [http://it.archive.ubuntu.com/ubuntu/dists/feisty/Release](http://it.archive.ubuntu.com/ubuntu/dists/feisty/Release) Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)"

i've tryed to write the original repository in "etc/apt/source.list" but when then i write in a terminal "sudo apt-get update" this is the error that i received:

```
ne0h@ME0W:~$ sudo apt-get update
Get:1 http://it.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://it.archive.ubuntu.com feisty/deb-src Translation-it                 
Get:2 http://archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-it        
Ign http://it.archive.ubuntu.com feisty/http://it.archive.ubuntu.com/ubuntu/ Translation-it
Ign http://it.archive.ubuntu.com feisty/feisty Translation-it                 
Get:3 http://it.archive.ubuntu.com feisty/universe Translation-it [43,8kB]
Get:4 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/restricted Translation-it       
Ign http://archive.ubuntu.com feisty-updates/http://it.archive.ubuntu.com/ubuntu/ Translation-it
Ign http://archive.ubuntu.com feisty-updates/deb-src Translation-it            
Ign http://archive.ubuntu.com feisty-updates/feisty Translation-it             
Ign http://archive.ubuntu.com feisty-updates/universe Translation-it           
Ign http://archive.ubuntu.com feisty-updates/main Translation-it
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-it
Ign http://security.ubuntu.com feisty-security/http://it.archive.ubuntu.com/ubuntu/ Translation-it
Ign http://security.ubuntu.com feisty-security/deb-src Translation-it          
Ign http://security.ubuntu.com feisty-security/feisty Translation-it           
Ign http://security.ubuntu.com feisty-security/universe Translation-it         
Ign http://security.ubuntu.com feisty-security/main Translation-it
Ign http://security.ubuntu.com feisty-security/multiverse Translation-it
Get:5 http://archive.ubuntu.com feisty-proposed Release.gpg [191B]             
Ign http://archive.ubuntu.com feisty-proposed/restricted Translation-it        
Ign http://archive.ubuntu.com feisty-proposed/http://it.archive.ubuntu.com/ubuntu/ Translation-it
Ign http://archive.ubuntu.com feisty-proposed/deb-src Translation-it           
Get:6 http://it.archive.ubuntu.com feisty/multiverse Translation-it [707B]     
Get:7 http://it.archive.ubuntu.com feisty/restricted Translation-it [14B]      
Get:8 http://it.archive.ubuntu.com feisty/main Translation-it [50,6kB]        
Ign http://archive.ubuntu.com feisty-proposed/feisty Translation-it            
Ign http://archive.ubuntu.com feisty-proposed/universe Translation-it          
Hit http://security.ubuntu.com feisty-security Release                         
Ign http://archive.ubuntu.com feisty-proposed/main Translation-it              
Ign http://archive.ubuntu.com feisty-proposed/multiverse Translation-it
Get:9 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-it       
Get:10 http://it.archive.ubuntu.com feisty/main Translation-it [50,6kB]        
74% [8 Translation-it bzip2 0] [10 Translation-it 681/50,6kB 1%] [In attesa deg
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign http://it.archive.ubuntu.com feisty/main Translation-it                    
Ign http://archive.ubuntu.com feisty-backports/http://it.archive.ubuntu.com/ubuntu/ Translation-it
Ign http://archive.ubuntu.com feisty-backports/deb-src Translation-it          
Ign http://archive.ubuntu.com feisty-backports/feisty Translation-it           
Ign http://archive.ubuntu.com feisty-backports/universe Translation-it         
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Get:11 http://it.archive.ubuntu.com feisty-backports Release.gpg [191B]        
Ign http://it.archive.ubuntu.com feisty-backports/main/debian-installer Translation-it
Hit http://it.archive.ubuntu.com feisty Release                  
Ign http://archive.ubuntu.com feisty-backports/main Translation-it
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-it
Hit http://archive.ubuntu.com feisty-updates Release 
Hit http://archive.ubuntu.com feisty-proposed Release
Hit http://archive.ubuntu.com feisty-backports Release
Hit http://it.archive.ubuntu.com feisty-backports Release                      
Hit http://archive.ubuntu.com feisty-updates/restricted Packages               
Hit http://it.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Hit http://archive.ubuntu.com feisty-proposed/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Scaricato 146kB in 1s (112kB/s)
Impossibile ottenere http://it.archive.ubuntu.com/ubuntu/dists/feisty/Release  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Impossibile ottenere http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release  Unable to find expected entry  http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages in Meta-index file (malformed Release file?)
Impossibile ottenere http://security.ubuntu.com/ubuntu/dists/feisty-security/Release  Unable to find expected entry  http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages in Meta-index file (malformed Release file?)
Impossibile ottenere http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/Release  Unable to find expected entry  http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages in Meta-index file (malformed Release file?)
Impossibile ottenere http://archive.ubuntu.com/ubuntu/dists/feisty-backports/Release  Unable to find expected entry  http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages in Meta-index file (malformed Release file?)
Lettura della lista dei pacchetti in corso... Fatto
W: Duplicate sources.list entry http://it.archive.ubuntu.com feisty/main Translation-it (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_feisty_main_i18n_Translation-it)
W: È consigliabile eseguire apt-get update per correggere questi problemi
E: Impossibile scaricare alcune file di indice, essi verranno ignorati, oppure si useranno quelli precedenti.
ne0h@ME0W:~$ 


```


in this situation i can't install every new application, my source.list file have problems!!! thank you and please help me!!!

bye, 
ne0hit

---

### Post by Sef on 2007-10-24
I would get another copy of the souces list and put that in your source list.  It seems that you got duplicate entries.

---

### Post by ne0hit on 2007-10-24
i have erase my source list, and i put in the original repo, than i have update, but this is the error:

[http://it.archive.ubuntu.com/ubuntu/dists/feisty/Release:](http://it.archive.ubuntu.com/ubuntu/dists/feisty/Release:) Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release:) Unable to find expected entry  [http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages](http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages) in Meta-index file (malformed Release file?)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/Release:](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release:) Unable to find expected entry  [http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages](http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages) in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/Release:](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/Release:) Unable to find expected entry  [http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages](http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages) in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/feisty-backports/Release:](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/Release:) Unable to find expected entry  [http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages](http://it.archive.ubuntu.com/ubuntu//binary-i386/Packages) in Meta-index file (malformed Release file?)

---

### Post by DonovanM11 on 2007-11-04
I have a similar problem.

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_feisty-commercial_main_binary-i386_Packages)

 when i run "cat /etc/apt/sources.list" I get

#
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

I have feisty fawn 7.04 and trying to upgrade to gusty gibbons 7.10

---

