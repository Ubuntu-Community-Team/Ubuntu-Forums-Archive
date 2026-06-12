---
title: "Repositories won't update"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by baldurmen on 2011-12-17
Yop,

When running "sudo apt-get update" I get this error:

> 
ubuntu@ubuntu-Ultra-UX:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1347 B]                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease 
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [765 B]
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-fr
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-fr
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-fr
Fetched 2310 B in 4s (503 B/s)
W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


The last thing I did before this was intall AHeck PPA...

Trying to update via Update Manager also gives me a repository error.

---

### Post by bluexrider on 2011-12-17
thats because the aheck PPA for Oneiric DOES NOT EXIST. You will need to edit the file 

[jaunty/]("http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/jaunty/")
[karmic/]("http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/karmic/")
[lucid/]("http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/lucid/")

NO ONEIRIC/

---

### Post by baldurmen on 2011-12-17
Joy.

What must I do now? Instinctively, I would:

1) go and modify /ect/apt/sources.list to delete any metion of aheck PPA

2) Update

3) Install PPA-Purge

4) Purge aheck PPA

Am I right?

---

### Post by bluexrider on 2011-12-17
> **baldurmen said:**
> Joy.

What must I do now? Instinctively, I would:

1) go and modify /ect/apt/sources.list to delete any metion of aheck PPA

2) Update

3) Install PPA-Purge

4) Purge aheck PPA

Am I right?
OR

go to "Software Sources" and under "Other Software" tab scroll down to and find Aheck. UnCheck the box next to it.

```
sudo apt-get update && sudo apt-get upgrade
```

should fix it

---

### Post by baldurmen on 2011-12-18
XD thanks for all!!!

---

### Post by bluexrider on 2011-12-18
> **baldurmen said:**
> XD thanks for all!!!

U R welcome

Please mark this 

(SOLVED)

---

