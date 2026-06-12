---
title: "Aptitude Repo Translations"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by Abaddon on 2007-01-13
While trying to dist-upgrade with OpenOffice 2.1, I ran into some [problems]("http://ubuntuforums.org/showthread.php?t=335406").

I've now noticed the following problem when I **sudo aptitude update**:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]               
**Ign http://security.ubuntu.com edgy-security/universe Translation-en_AU    **     
Ign http://flomertens.keo.in edgy Release.gpg                                   
Get:2 http://kubuntu.org edgy Release.gpg [189B]                                
Ign http://kubuntu.org edgy/main Translation-en_AU                              
Get:3 http://archive.canonical.com dapper-commercial Release.gpg [191B]         
[B]Ign http://archive.canonical.com dapper-commercial/main Translation-en_AU       
Ign http://security.ubuntu.com edgy-security/main Translation-en_AU             
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_AU       
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_AU [/B]      
Hit http://security.ubuntu.com edgy-security Release                            
Get:4 http://repository.debuntu.org edgy Release.gpg [189B]                     
Hit http://kubuntu.org edgy Release                                             
Hit http://archive.canonical.com dapper-commercial Release                      
Get:5 http://gandalfn.club.fr edgy Release.gpg [189B]                           
Get:6 http://au.archive.ubuntu.com edgy Release.gpg [191B]                      
**Ign http://flomertens.keo.in edgy/main Translation-en_AU      **                  
Hit http://security.ubuntu.com edgy-security/universe Packages                  
[B]Ign http://repository.debuntu.org edgy/multiverse Translation-en_AU             
Ign http://gandalfn.club.fr edgy/stable Translation-en_AU        [/B]               
Hit http://security.ubuntu.com edgy-security/main Packages                      
Hit http://security.ubuntu.com edgy-security/multiverse Packages                
Hit http://security.ubuntu.com edgy-security/restricted Packages                
Hit http://kubuntu.org edgy/main Packages                                       
Hit http://security.ubuntu.com edgy-security/universe Sources                   
Hit http://security.ubuntu.com edgy-security/main Sources                       
Hit http://security.ubuntu.com edgy-security/multiverse Sources                 
Hit http://security.ubuntu.com edgy-security/restricted Sources                 
Hit http://repository.debuntu.org edgy Release                                  
[B]Ign http://au.archive.ubuntu.com edgy/universe Translation-en_AU                
Ign http://gandalfn.club.fr edgy/dev Translation-en_AU      [/B]                    
Hit http://archive.canonical.com dapper-commercial/main Packages                
Hit http://repository.debuntu.org edgy/multiverse Packages                      
**Ign http://au.archive.ubuntu.com edgy/main Translation-en_AU     **               
Hit http://gandalfn.club.fr edgy Release                                        
Ign http://flomertens.keo.in edgy Release                                       
**Ign http://au.archive.ubuntu.com edgy/multiverse Translation-en_AU   **           
Hit http://repository.debuntu.org edgy/multiverse Sources                       
Hit http://gandalfn.club.fr edgy/stable Packages                                
Ign http://flomertens.keo.in edgy/main Packages                      
**Ign http://au.archive.ubuntu.com edgy/restricted Translation-en_AU **         
Hit http://gandalfn.club.fr edgy/dev Packages                                   
Get:7 http://au.archive.ubuntu.com edgy-backports Release.gpg [191B] 
Hit http://flomertens.keo.in edgy/main Packages                                 
[B]Ign http://au.archive.ubuntu.com edgy-backports/main Translation-en_AU          
Ign http://au.archive.ubuntu.com edgy-backports/restricted Translation-en_AU                                                                                 
Ign http://au.archive.ubuntu.com edgy-backports/universe Translation-en_AU                                                                                   
Ign http://au.archive.ubuntu.com edgy-backports/multiverse Translation-en_AU [/B]                                                                                
Get:8 http://au.archive.ubuntu.com edgy-updates Release.gpg [191B]                                                                                           
[B]Ign http://au.archive.ubuntu.com edgy-updates/universe Translation-en_AU                                                                                     
Ign http://au.archive.ubuntu.com edgy-updates/main Translation-en_AU                                                                                         
Ign http://au.archive.ubuntu.com edgy-updates/multiverse Translation-en_AU                                                                                   
Ign http://au.archive.ubuntu.com edgy-updates/restricted Translation-en_AU    [/B]                                                                               
Get:9 http://au.archive.ubuntu.com edgy-proposed Release.gpg [191B]                                                                                          
[B]Ign http://au.archive.ubuntu.com edgy-proposed/universe Translation-en_AU                                                                                    
Ign http://au.archive.ubuntu.com edgy-proposed/main Translation-en_AU                                                                                        
Ign http://au.archive.ubuntu.com edgy-proposed/multiverse Translation-en_AU                                                                                  
Ign http://au.archive.ubuntu.com edgy-proposed/restricted Translation-en_AU[/B]                                                                                  
Hit http://au.archive.ubuntu.com edgy Release                                                                                                                
Hit http://au.archive.ubuntu.com edgy-backports Release                                                                                                      
Hit http://au.archive.ubuntu.com edgy-updates Release                                                                                                        
Hit http://au.archive.ubuntu.com edgy-proposed Release                                                                                                       
Hit http://au.archive.ubuntu.com edgy/universe Packages                                                                                                      
Hit http://au.archive.ubuntu.com edgy/main Packages                                                                                                          
Hit http://au.archive.ubuntu.com edgy/multiverse Packages                                                                                                    
Hit http://au.archive.ubuntu.com edgy/restricted Packages                                                                                                    
Hit http://au.archive.ubuntu.com edgy/universe Sources                                                                                                       
Hit http://au.archive.ubuntu.com edgy/main Sources                                                                                                           
Hit http://au.archive.ubuntu.com edgy/multiverse Sources                                                                                                     
Hit http://au.archive.ubuntu.com edgy/restricted Sources                                                                                                     
Hit http://au.archive.ubuntu.com edgy-backports/main Packages                                                                                                
Hit http://au.archive.ubuntu.com edgy-backports/restricted Packages                                                                                          
Hit http://au.archive.ubuntu.com edgy-backports/universe Packages                                                                                            
Hit http://au.archive.ubuntu.com edgy-backports/multiverse Packages                                                                                          
Hit http://au.archive.ubuntu.com edgy-backports/restricted Sources                                                                                           
Hit http://au.archive.ubuntu.com edgy-backports/main Sources                                                                                                 
Hit http://au.archive.ubuntu.com edgy-backports/multiverse Sources                                                                                           
Hit http://au.archive.ubuntu.com edgy-backports/universe Sources                                                                                             
Hit http://au.archive.ubuntu.com edgy-updates/universe Packages                                                                                              
Hit http://au.archive.ubuntu.com edgy-updates/main Packages                                                                                                  
Hit http://au.archive.ubuntu.com edgy-updates/multiverse Packages                                                                                            
Hit http://au.archive.ubuntu.com edgy-updates/restricted Packages                                                                                            
Hit http://au.archive.ubuntu.com edgy-updates/universe Sources                                                                                               
Hit http://au.archive.ubuntu.com edgy-updates/main Sources                                                                                                   
Hit http://au.archive.ubuntu.com edgy-updates/multiverse Sources                                                                                             
Hit http://au.archive.ubuntu.com edgy-updates/restricted Sources                                                                                             
Hit http://au.archive.ubuntu.com edgy-proposed/universe Packages                                                                                             
Hit http://au.archive.ubuntu.com edgy-proposed/main Packages                                                                                                 
Hit http://au.archive.ubuntu.com edgy-proposed/multiverse Packages                                                                                           
Hit http://au.archive.ubuntu.com edgy-proposed/restricted Packages                                                                                           
Hit http://au.archive.ubuntu.com edgy-proposed/universe Sources                                                                                              
Hit http://au.archive.ubuntu.com edgy-proposed/main Sources                                                                                                  
Hit http://au.archive.ubuntu.com edgy-proposed/multiverse Sources                                                                                            
Hit http://au.archive.ubuntu.com edgy-proposed/restricted Sources                                                                                            
Fetched 9B in 30s (0B/s)                                            
```


Notice all the Translation-en_AU lines - which don't actually work at all.  Now last time I checked, Australian English was a pretty good approximation of English elsewhere in the world.

How can I stop aptitude from looking for these translations and slowing down my update time?

Thanks,

---

### Post by ajmorris on 2007-01-13
"sudo gedit /etc/apt/sources.list" (in a terminal) then comment out the lines (add a # to the front of them) now they will not be checked for.

---

### Post by pay on 2007-01-13
You would have to comment out the repos that you didn't want. Anyway, Australia english is slightly different to US Egnlish. For Example, Australians spell colour, US spells color.

---

### Post by Abaddon on 2007-01-13
> **ajmorris said:**
> "sudo gedit /etc/apt/sources.list" (in a terminal) then comment out the lines (add a # to the front of them) now they will not be checked for.

But the problem is these are the generic lines in  my sources - Ubuntu decides to automatically look for en_AU translations from my generic sources.list... here is is for reference (sorry - should have been with the first post)

```
deb http://au.archive.ubuntu.com/ubuntu/ edgy universe main multiverse restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy universe main multiverse restricted

deb http://au.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe

deb http://security.ubuntu.com/ubuntu/ edgy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ edgy-security universe main multiverse restricted

deb http://au.archive.ubuntu.com/ubuntu/ edgy-updates universe main multiverse restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-updates universe main multiverse restricted

deb http://au.archive.ubuntu.com/ubuntu/ edgy-proposed universe main multiverse restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-proposed universe main multiverse restricted

#Amarok with MTP support
deb http://kubuntu.org/packages/amarok-144 edgy main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://gandalfn.club.fr/ubuntu edgy stable dev

# ntfs-3g Repo - see http://www.ubuntuforums.org/showthread.php?t=217009
deb http://flomertens.keo.in/ubuntu/ edgy main

deb http://repository.debuntu.org/ edgy multiverse
deb-src http://repository.debuntu.org/ edgy multiverse

```

Note that Ubuntu first searches for the non-existent en_AU translation, fails, and then goes and loads the repo.  This is the "feature" I'd like to do away with, without changing my default language back.

> You would have to comment out the repos that you didn't want. Anyway, Australia english is slightly different to US Egnlish. For Example, Australians spell colour, US spells color

Yes, but you don't need a separate translation for Australian english... you just grin and bear the missing letters :-)

---

### Post by ajmorris on 2007-01-13
how did you set yours to get the AU ones? Mine gets the US ones but my default language is Australian.

---

### Post by Abaddon on 2007-01-13
> **ajmorris said:**
> how did you set yours to get the AU ones? Mine gets the US ones but my default language is Australian.

I didn't set it - that's the problem.  I want to un-set it!
](*,)

---

### Post by ajmorris on 2007-01-13
Sorry i'm stumpted. :( :confused:

---

### Post by ajmorris on 2007-01-13
i hope you are still looking at this post.... I found the answer. I did some playing around and managed to get mine to get the AU as well. To fix this go to a command line and type

"sudo apt-get update --fix-missing"

Worked for me... hope it works for you. :D

---

### Post by Abaddon on 2007-01-17
> **ajmorris said:**
> i hope you are still looking at this post.... I found the answer. I did some playing around and managed to get mine to get the AU as well. To fix this go to a command line and type

"sudo apt-get update --fix-missing"

Worked for me... hope it works for you. :D

Thanks for the extra suggestion, but alas, no, it didn't.

---

### Post by tallman9 on 2007-02-23
I would also like to know how to unset this search for en_AU translations in apt-get and aptitude....I live in an European country and have nothing to do with Australia =)

---

