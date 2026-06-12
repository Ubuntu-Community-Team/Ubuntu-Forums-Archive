---
title: "Duplicate sources.list entry in ubuntu 12.04"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by yrohinkumar on 2012-05-16
I know it's a noob question...but it is bothering me for a while...I'm sure I'm missing something here...

I keep getting this every time I try to update...:mad:

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I tried removing that file /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages 

looked into sources.list to remove the mentioned duplicate entry...but I couldn't find one...!!! 

Any ideas???

---

### Post by wilee-nilee on 2012-05-16
Use crtl-f to search for the extra in.

```
 sudo gedit /etc/apt/sources.list
```

---

### Post by yrohinkumar on 2012-05-16
Thanks for the quick reply...

I presume u were talking about this entry "deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main" which was the only one containing the word 'extra'... I disabled it...but with no luck...**the error persists...**

btw I noticed 'sources.list~' file and 'sources.list.d/' in the same folder...the entries in those are counted too???

---

### Post by wilee-nilee on 2012-05-16
> **yrohinkumar said:**
> Thanks for the quick reply...

I presume u were talking about this entry "deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main" which was the only one containing the word 'extra'... I disabled it...but with no luck...**the error persists...**

btw I noticed 'sources.list~' file and 'sources.list.d/' in the same folder...the entries in those are counted too???

Only you will know the extra, run a update in the terminal and post all of it, Extra will not be in the actual list it is saying you have an extra in the terminal as a communication.

Also post this 

cat /etc/apt/sources.list

---

### Post by yrohinkumar on 2012-05-16
This is what I have... (Sorry for the mess...I've been updating distros since long time ago and have problem managing huge list of repos...)

```
Ign http://dl.google.com stable InRelease
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.canonical.com precise InRelease                             
Ign http://dl.google.com stable InRelease                            
Ign http://in.archive.ubuntu.com precise InRelease                   
Ign http://in.archive.ubuntu.com precise-updates InRelease           
Ign http://in.archive.ubuntu.com precise-backports InRelease         
Hit http://security.ubuntu.com precise-security Release.gpg          
Get:1 http://archive.canonical.com precise Release.gpg [198 B]       
Get:2 http://dl.google.com stable Release.gpg [198 B]                
Hit http://in.archive.ubuntu.com precise Release.gpg                           
Hit http://security.ubuntu.com precise-security Release                        
Get:3 http://archive.canonical.com precise Release [7,078 B]                   
Hit http://in.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://in.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Get:4 http://archive.canonical.com precise/partner i386 Packages [4,999 B]     
Hit http://in.archive.ubuntu.com precise Release                               
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://in.archive.ubuntu.com precise-updates Release                       
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://in.archive.ubuntu.com precise-backports Release                     
Hit http://in.archive.ubuntu.com precise/main i386 Packages                    
Hit http://in.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://in.archive.ubuntu.com precise/universe i386 Packages                
Hit http://in.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://in.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://in.archive.ubuntu.com precise/multiverse TranslationIndex        
Hit http://in.archive.ubuntu.com precise/restricted TranslationIndex        
Hit http://in.archive.ubuntu.com precise/universe TranslationIndex          
Hit http://in.archive.ubuntu.com precise-updates/main i386 Packages         
Hit http://in.archive.ubuntu.com precise-updates/restricted i386 Packages   
Hit http://in.archive.ubuntu.com precise-updates/universe i386 Packages     
Hit http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages   
Hit http://in.archive.ubuntu.com precise-updates/main TranslationIndex      
Hit http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://in.archive.ubuntu.com precise-updates/universe TranslationIndex  
Hit http://in.archive.ubuntu.com precise-backports/main Sources             
Hit http://in.archive.ubuntu.com precise-backports/restricted Sources       
Hit http://in.archive.ubuntu.com precise-backports/universe Sources         
Hit http://in.archive.ubuntu.com precise-backports/multiverse Sources       
Hit http://in.archive.ubuntu.com precise/main Translation-en                
Hit http://in.archive.ubuntu.com precise/multiverse Translation-en          
Hit http://in.archive.ubuntu.com precise/restricted Translation-en          
Hit http://in.archive.ubuntu.com precise/universe Translation-en            
Hit http://in.archive.ubuntu.com precise-updates/main Translation-en        
Hit http://in.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://in.archive.ubuntu.com precise-updates/restricted Translation-en  
Hit http://in.archive.ubuntu.com precise-updates/universe Translation-en    
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://archive.canonical.com precise/partner Translation-en
Get:5 http://dl.google.com stable Release.gpg [198 B]
Get:6 http://dl.google.com stable Release [1,347 B]                            
Get:7 http://dl.google.com stable Release [1,347 B]                            
Get:8 http://dl.google.com stable/main i386 Packages [1,236 B]                 
Get:9 http://dl.google.com stable/main i386 Packages [1,236 B]                 
Ign http://dl.google.com stable/main TranslationIndex
Get:10 http://dl.google.com stable/main i386 Packages [769 B]
Ign http://dl.google.com stable/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Fetched 17.4 kB in 2min 12s (130 B/s)                                          
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

thanks once again...:)

---

### Post by wilee-nilee on 2012-05-17
Now post this,

cat /etc/apt/sources.list

---

### Post by yrohinkumar on 2012-05-17
```

# added by the release upgrader
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423.2)]/ precise main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ precise main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ precise universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ precise multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu precise-security main restricted
# deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
# deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
# deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

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

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb-src http://extras.ubuntu.com/ubuntu oneiric main
# deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe


```

Told u it is a mess :)

---

### Post by wilee-nilee on 2012-05-17
open this again.

sudo gedit /etc/apt/sources.list

Hit crtl-f and put in this in to search.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

This I think is the double entry

---

### Post by yrohinkumar on 2012-05-17
Thanks a lot for seeing the problem through the end... it worked...the error message was kinda misleading...but thanks again for patiently looking this through... :)

---

### Post by wilee-nilee on 2012-05-17
> **yrohinkumar said:**
> Thanks a lot for seeing the problem through the end... it worked...the error message was kinda misleading...but thanks again for patiently looking this through... :)

No problem it took me a minute to figure it out, I just did the same search with the whole line and used the back space and removed one letter at a time.

---

### Post by synctext on 2012-05-30
+1
Thnx for this fix, it worked. I had the same problem and removed these 2 double entries:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

---

### Post by terdegstra on 2012-07-03
S="/etc/apt/sources.list" ; S2="$S ${S}.d/*.list" ; grep -b "^deb`cat $S2 | grep -i "^deb[[:space:]]http" | sort | uniq -dc | sed -e 's;[[:space:]]\+[[:digit:]]\+[[:space:]]\+deb\(.\+$\);\1;g'`$" $S2

---

### Post by lcniuren33 on 2012-10-01
Thanks a lot, I have the same problem and solved following your method~:guitar:

---

### Post by Alex.Pi on 2013-01-08
hi,
I have the same problem but I do not have this string in the file, so I do not know what to remove. 

sorry for confusion, I have found it and all works.
Thank you.

---

### Post by Wim Jansen on 2013-04-15
Hello Ubuntu-guru,

After several days of troubleshooting on this "Duplicate" problem I finality found your solution, and it worked.

Thank you very, very much, regards,

Wim Jansen - Hummelo (That's in "De Achterhoek")

---

### Post by ibjsb4 on 2013-04-15
Hi Wim

Something that may help in future searches

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Duplicate+sources.list+entry&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Duplicate+sources.list+entry&sa=Search&cof=FORID:9)

And welcome to the forums :)

---

