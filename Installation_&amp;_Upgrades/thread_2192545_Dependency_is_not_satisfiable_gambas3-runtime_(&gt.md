---
title: "Dependency is not satisfiable: gambas3-runtime (&gt;=3.0.90)"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by trevino.alan90 on 2013-12-08
For any app that I try to install, I get this error.

> [B]
Dependency is not satisfiable: gambas3-runtime (>=3.0.90)[/B]


This also applies to any app, like Yumi, that I download off the web.

Any ideas as to what is causing this and how to fix it?

Thanks!

---

### Post by ian-weisser on 2013-12-08
```
$ rmadison -u ubuntu gambas3-runtime
 gambas3-runtime | 3.1.1-2ubuntu5   | quantal/universe | amd64, armel, armhf, i386, powerpc
 gambas3-runtime | 3.1.1-2ubuntu6   | raring/universe  | amd64, armhf, i386, powerpc
 gambas3-runtime | 3.1.1-2ubuntu8   | saucy/universe   | amd64, armhf, i386, powerpc
 gambas3-runtime | 3.1.1-2.2ubuntu2 | trusty/universe  | amd64, arm64, armhf, i386, powerpc
```

Since that package was added to the Ubuntu repositories in 12.10, one possible answer is that you are running 10.04 or 12.04.
Those LTS releases are intended for the long-term stability of mature production systems that don't want to change across years. If you are installing newer software, perhaps you should be using a newer release of Ubuntu.

Software, like Yumi, that is not in the Ubuntu Repositories is not supported by this community...though we'll try as best we can. Non-Ubuntu software is supported by the project or individual that you downloaded it from.

[B]Your package manager is broken.
**You are not receiving security updates.**[/B] 
You will not be able to install, remove, or update any software using *any* means (except compiling from source) until you fix it.

To fix the problem, please show us an *entire* terminal session showing the error. We need the context.
Open a terminal and try the following command and show us the complete result, including any garbage you don't understand.```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by trevino.alan90 on 2013-12-08
I am running 12.04 because this is what my company uses at work for testing, advanced operations, etc. I figured it would be a good idea to learn how to use it.

This is what that sudo command gave me.

> 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Fetched 72 B in 2s (33 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 

---

### Post by trevino.alan90 on 2013-12-08
Also, should I update to 13.10 or 13.04? I have both .ISO files.

---

### Post by ian-weisser on 2013-12-08
Well, that's much better news than usual in such cases.
Perhaps the package manager isn't broken after all.
Perhaps you are indeed getting security updates.

We'll see. Please show the output of ```
sudo dpkg --configure -a
```

---

### Post by trevino.alan90 on 2013-12-08
Well, this is funny. There is no output. It's still not letting me install anything. I tested this with gparted

---

### Post by ian-weisser on 2013-12-08
No output is a good thing. It means your system seems just fine.
How do you reproduce the error?
Can you reproduce the error on the command line, and show us that session, for the offending command through the entire output?

(Of course, if you *can't* reproduce the error, that's also good news!)

---

### Post by trevino.alan90 on 2013-12-09
I am still having the same error. I am doing it through the Ubuntu software Center. Although, I have been able to install Chrome VIA Terminal.

---

### Post by trevino.alan90 on 2013-12-09
This is really silly of me, but I didn't run the first terminal code you had started with. I ran this code and it prompted me with an installation.
> rmadison -u ubuntu gambas3-runtime 

I am now able to install applications! I just installed GParted Partition Editor.

---

