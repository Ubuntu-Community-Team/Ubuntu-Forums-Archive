---
title: "Upgrade problem: Dapper to Edgy: Alt CD"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by derby007 on 2007-01-04
In my attempt to update to Edgy from Dapper, i am nearly there but........i now have an error with it recognising the Alternate CD (as this is my only option for upgrading) if i want to add a program, like GEdit....

Problem:

It is giving me an error that it wants a certain type of Ubuntu Edgy: ie. >

Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)

compared to:

Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) 

Note: i've only ever had 1 type of Alt CD, but both are mentioned in my sources.list, but i don't know how? Any ideas?

---

### Post by derby007 on 2007-01-05
Can anyone tell me why I'm seeing 2 versions of Ubuntu Edgy ?

---

### Post by aysiu on 2007-01-05
I can't tell you why, but I can tell you what you should do.

Go to System > Administration > Synaptic > Settings > Repositories and uncheck **all** the boxes next to your sources.

Then go to Edit > Add CD-ROM

and finally, in the terminal, ```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by derby007 on 2007-01-05
Cheers, i did this 'after' i had read your links and other peoples advise, but i didn't do it until after i had already tried to upgrade, doh, and its giving me errors now, doh. 
I'm just wondering why its looking for the : Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1), 
ie. .1 version, 
do i need to get another version of Alt CD, a more up to date one perhaps??

---

