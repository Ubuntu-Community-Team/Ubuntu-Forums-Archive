---
title: "Ubuntu update error"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by Bray90820 on 2012-02-12
so earlier today i generated a new source apt list and now when i run sudo apt-get update i get some errors i am running Ubuntu 11.10

```
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu InRelease               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease              
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu Release.gpg             
Get:3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,249 B]      
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,242 B]                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                      
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu Release                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/main TranslationIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/oneiric TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main amd64 Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/oneiric Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/oneiric amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/oneiric i386 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/oneiric Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) http/ppa/ubuntu/oneiric Translation-en
Fetched 4,036 B in 2s (1,534 B/s)
W: Failed to fetch [http://ppa.launchpad.net/dists/http/ppa/ubuntu/oneiric/source/Sources](http://ppa.launchpad.net/dists/http/ppa/ubuntu/oneiric/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/dists/http/ppa/ubuntu/main/source/Sources](http://ppa.launchpad.net/dists/http/ppa/ubuntu/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/dists/http/ppa/ubuntu/oneiric/binary-amd64/Packages](http://ppa.launchpad.net/dists/http/ppa/ubuntu/oneiric/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/dists/http/ppa/ubuntu/main/binary-amd64/Packages](http://ppa.launchpad.net/dists/http/ppa/ubuntu/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/dists/http/ppa/ubuntu/oneiric/binary-i386/Packages](http://ppa.launchpad.net/dists/http/ppa/ubuntu/oneiric/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/dists/http/ppa/ubuntu/main/binary-i386/Packages](http://ppa.launchpad.net/dists/http/ppa/ubuntu/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by plucky on 2012-02-13
Post the new sources.list ```
cat /etc/apt/sources.list
``` and ```
ls -l /etc/apt/sources.list.d/
```.

The "404  Not Found" probably means one of your sources doesn't exist.


Good Luck

---

### Post by zvacet on 2012-02-13
Remove PPA from your source list and run


```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cortman on 2012-02-13
The repositories that are generating errors don't exist. Did you add these manually?
Also, they appear to be for the standard Ubuntu repositories (main, restricted, universe, etc.). The REAL repositories were update successfully as shown near the top of the list. Remove all the repositories that have errors by running

```
gksu gedit /etc/apt/sources.list
```

Delete the whole line containing the erroneous repository info. Then run

```
sudo rm -r /var/lib/apt/lists/*
sudo apt-get update
```

See if that fixes it. Good luck!

---

### Post by raja.genupula on 2012-02-13
+1 to all solutions. 

But what i am thinking is how it would be if we change server to main one or a good nearer server  and then try again . If thats not help us then we can go for remaining above solutions . 

:):)

---

### Post by Bray90820 on 2012-02-13
i tried all of your suggestions but none of them worked the sources are still not found

---

### Post by cortman on 2012-02-13
> **Bray90820 said:**
> i tried all of your suggestions but none of them worked the sources are still not found

zvacet and I gave basically the same instruction, mine is just a little more detailed. If you opened up sources.list with a text editor, removed ALL the offending PPA's, it WILL fix your problem. Did you run

```
sudo apt-get update
```

after you edited sources.list?

---

### Post by Bray90820 on 2012-02-13
well i went into my sources.list and tried to find my bad ppa but the weren't in there could it possibly be that i added a badsig  when i generated my new sources.list

---

### Post by Bray90820 on 2012-02-13
solved the authentication was messed up i removed all my keys and re added them

---

