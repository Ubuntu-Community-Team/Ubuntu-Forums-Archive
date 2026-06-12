---
title: "Update manager errors"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by siddi on 2012-12-05
I have red danger message on my main toolbar and it says error: broken count>0

and it also says the installed packags have unmet dependancies

Further i am not able to run update manager cos it says 'this package is broken' and is asking me to disable third party repositories which i don;t know how to.

In the details it says the following packages have unmet dependancies.... but is blank below.

My facebook page is getting ads on top witth loud sounds and i think my ubuntu has downloaded unwanted stuff

Please help

---

### Post by zvacet on 2012-12-05
From terminal 

```
sudo apt-get -f install
```

---

### Post by ibjsb4 on 2012-12-05
Starting with post #16

[http://ubuntuforums.org/showthread.php?t=1950784&page=3](http://ubuntuforums.org/showthread.php?t=1950784&page=3)

---

### Post by siddi on 2012-12-06
siddharth@siddharth-Aspire-5570:~$ sudo apt-get -f install
[sudo] password for siddharth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package update-manager needs to be reinstalled, but I can't find an archive for it.
siddharth@siddharth-Aspire-5570:~$

---

### Post by zvacet on 2012-12-06
```
sudo apt-get --reinstall install update-manager-core
```

---

### Post by siddi on 2012-12-07
I am still getting the same response

siddharth@siddharth-Aspire-5570:~$ sudo apt-get --reinstall install update-manager-core
[sudo] password for siddharth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package update-manager needs to be reinstalled, but I can't find an archive for it.
siddharth@siddharth-Aspire-5570:~$

I am not able to open software center too

---

### Post by zvacet on 2012-12-07
```
sudo apt-get --fix-missing install
```

---

### Post by siddi on 2012-12-07
Still the same response

siddharth@siddharth-Aspire-5570:~$ sudo apt-get --fix-missing install
[sudo] password for siddharth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package update-manager needs to be reinstalled, but I can't find an archive for it.
siddharth@siddharth-Aspire-5570:~$

---

### Post by zvacet on 2012-12-08
I running out of ideas.Try 

```
sudo apt-get install --reinstall update-manager
```

---

### Post by siddi on 2012-12-08
siddharth@siddharth-Aspire-5570:~$ sudo apt-get install --resintall update-manager
[sudo] password for siddharth: 
E: Command line option --resintall is not understood
siddharth@siddharth-Aspire-5570:~$ sudo apt-get install --reinstall update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package update-manager needs to be reinstalled, but I can't find an archive for it.
siddharth@siddharth-Aspire-5570:~$

---

### Post by Capt_Zaphod on 2012-12-09
I have the same string of errors.

---

### Post by LuisGMarine on 2012-12-09
Try updating the repo list with;

```
sudo apt-get update
```

and then try the previous command again, if it still spits out the same problem try this:

```
sudo dpkg --remove --force-remove-reinstreq update-manager
```

then if that works you should reinstall it with:

```
sudo apt-get install update-manager
```

SOURCES:
[http://ubuntuforums.org/showthread.php?t=1914982]("http://ubuntuforums.org/showthread.php?t=1914982")
[http://www.ubuntugeek.com/package-installation-error-and-solution.html]("http://www.ubuntugeek.com/package-installation-error-and-solution.html")

---

### Post by siddi on 2012-12-10
siddharth@siddharth-Aspire-5570:~$ sudo apt-get update
[sudo] password for siddharth: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid InRelease                               
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security InRelease                      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid InRelease                               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:3 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security Release.gpg [198 B]          
Get:4 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 InRelease                             
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,247 B]                 
Get:6 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates Release.gpg [198 B]           
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:7 [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release.gpg [189 B]                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid Release                                 
Get:8 [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release [113 kB]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:9 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security Release [57.3 kB]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:10 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:11 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates Release [58.3 kB]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner TranslationIndex                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                         
Get:12 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [6,026 B]    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Sources                            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main i386 Packages                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted i386 Packages                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe i386 Packages                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse i386 Packages               
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main TranslationIndex                  
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse TranslationIndex             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted TranslationIndex             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe TranslationIndex               
Get:13 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Sources [133 kB]       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Get:14 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Sources [1,267 B]
Get:15 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Sources [42.5 kB]  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Get:16 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Sources [2,350 B]
Get:17 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main i386 Packages [468 kB] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en_AU               
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en                  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_AU             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU                    
Get:18 [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main i386 Packages [11.8 kB]       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main TranslationIndex                 
Get:19 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted i386 Packages [2,867 B]
Get:20 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe i386 Packages [138 kB]
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en_AU                
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en                   
Get:21 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse i386 Packages [5,353 B]
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main TranslationIndex          
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse TranslationIndex    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted TranslationIndex    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe TranslationIndex      
Get:22 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main Sources [233 kB]        
Get:23 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted Sources [2,196 B] 
Get:24 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe Sources [105 kB]    
Get:25 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse Sources [5,827 B] 
Get:26 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main i386 Packages [663 kB]  
Get:27 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted i386 Packages [4,630 B]
Get:28 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe i386 Packages [284 kB]
Get:29 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse i386 Packages [11.5 kB]
Get:30 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main TranslationIndex [3,153 B]
Get:31 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse TranslationIndex [2,165 B]
Get:32 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted TranslationIndex [2,065 B]
Get:33 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe TranslationIndex [2,574 B]
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Translation-en_AU                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Translation-en_AU            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Translation-en_AU            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main Translation-en_AU          
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse Translation-en_AU    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted Translation-en_AU    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Translation-en                     
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Translation-en_AU
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Translation-en_AU
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Translation-en_AU
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Translation-en_AU
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Translation-en_AU
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Translation-en
Fetched 2,369 kB in 1min 27s (27.0 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/ailurus/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ailurus/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ailurus/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ailurus/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
siddharth@siddharth-Aspire-5570:~$ sudo apt-get install --reinstall update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package update-manager needs to be reinstalled, but I can't find an archive for it.
siddharth@siddharth-Aspire-5570:~$ dpkg --remove --force-remove-reinstreq update-manager
dpkg: error: requested operation requires superuser privilege
siddharth@siddharth-Aspire-5570:~$

---

### Post by ibjsb4 on 2012-12-10
Im going to try this one more time.  Please read and follow **post#3**.

---

### Post by Capt_Zaphod on 2012-12-10
> **ibjsb4 said:**
> Im going to try this one more time.  Please read and follow **post#3**.

I tried.
I went to the other thread and opened the Update Manager to make those adjustments but,when I open the update manager I get this error:
[INDENT]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/INDENT]

When I click on OK it closes the update manager.

I tried LuisGMarine's suggestion and it didn't work either.

---

### Post by Capt_Zaphod on 2012-12-10
> **LuisGMarine said:**
> Try updating the repo list with;

```
sudo apt-get update
```

and then try the previous command again, if it still spits out the same problem try this:

```
dpkg --remove --force-remove-reinstreq update-manager
```

then if that works you should reinstall it with:

```
sudo apt-get install update-manager
```

SOURCES:
[http://ubuntuforums.org/showthread.php?t=1914982]("http://ubuntuforums.org/showthread.php?t=1914982")
[http://www.ubuntugeek.com/package-installation-error-and-solution.html]("http://www.ubuntugeek.com/package-installation-error-and-solution.html")

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by ibjsb4 on 2012-12-10
@Capt_Zaphod

Open a terminal and enter:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

---

### Post by LuisGMarine on 2012-12-10
If that doesn't work, the command should have been:

```
sudo dpkg --remove --force-remove-reinstreq update-manager
```

---

### Post by Capt_Zaphod on 2012-12-10
> **ibjsb4 said:**
> @Capt_Zaphod

Open a terminal and enter:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```

That did it!

Thank you!

---

### Post by Capt_Zaphod on 2012-12-10
> **LuisGMarine said:**
> If that doesn't work, the command should have been:

```
sudo dpkg --remove --force-remove-reinstreq update-manager
```

Thank you.

---

### Post by siddi on 2012-12-11
I can't even open my update manager!!

---

### Post by siddi on 2012-12-11
iddharth@siddharth-Aspire-5570:~$ sudo dpkg --remove --force-remove-reinstreq update-manager
dpkg: dependency problems prevent removal of update-manager:
 ubuntu-desktop depends on update-manager.
 update-notifier depends on update-manager-gnome | update-manager; however:
  Package update-manager-gnome is not installed.
  Package update-manager is to be removed.
dpkg: error processing update-manager (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 update-manager
siddharth@siddharth-Aspire-5570:~$

---

### Post by NightsShadeQueen on 2012-12-11
Afaik, ubuntu-desktop doesn't...actually do anything; it just exists for the purposes of distro upgrades, so you can remove that too; just remember to put it back before you upgrade.

sudo dpkg --remove --force-remove-reinstreq --force-depends update-manager

might also work.

---

### Post by ibjsb4 on 2012-12-11
> **siddi said:**
> I can't even open my update manager!!

In terminal:

```
gksudo gedit /etc/apt/sources.list.d/*
```

And then comment out (#) offending entries to look something like this:

#[http://ppa.launchpad.net/ailurus/](http://ppa.launchpad.net/ailurus/)

#[http://ppa.launchpad.net/mozillateam/](http://ppa.launchpad.net/mozillateam/)

That is not how the full line will read in your sources list, but I think you will get the idea.  Just add that hash mark (#) at the beginning of the line.

Then save and close and follow with:

```
sudo apt-get update
```

Any errors now?

---

### Post by siddi on 2012-12-11
#deb [http://ppa.launchpad.net/ailurus/ppa/ubuntu](http://ppa.launchpad.net/ailurus/ppa/ubuntu) precise main
#deb-src [http://ppa.launchpad.net/ailurus/ppa/ubuntu](http://ppa.launchpad.net/ailurus/ppa/ubuntu) precise main

I have save this in the sources list

iddharth@siddharth-Aspire-5570:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid InRelease                               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid InRelease                               
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security InRelease                      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security Release.gpg                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main i386 Packages                    
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main TranslationIndex                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid Release                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner TranslationIndex                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates Release                         
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Sources                            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main i386 Packages                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted i386 Packages                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe i386 Packages                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse i386 Packages                
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main TranslationIndex                   
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse TranslationIndex             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted TranslationIndex             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe TranslationIndex               
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Sources                   
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Sources             
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Sources               
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Sources             
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main i386 Packages             
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted i386 Packages       
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe i386 Packages         
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse i386 Packages       
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main TranslationIndex          
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse TranslationIndex    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted TranslationIndex    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe TranslationIndex      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main i386 Packages              
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted i386 Packages        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe i386 Packages          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                         
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse i386 Packages        
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main TranslationIndex           
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse TranslationIndex     
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted TranslationIndex     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe TranslationIndex       
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Translation-en_AU                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Translation-en_AU  
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en_AU                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Translation-en_AU            
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                    
  404  Not Found
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en                   
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main Translation-en_AU
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse Translation-en_AU
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted Translation-en_AU
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en             
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en_AU
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_AU
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Translation-en_AU
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Translation-en_AU
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Translation-en_AU
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Translation-en_AU
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Translation-en
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Translation-en_AU
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Translation-en
N: Ignoring file 'Untitled Document 1' in directory '/etc/apt/sources.list.d/' as it has no filename extension
W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ibjsb4 on 2012-12-11
Comment out the other one too.

/mozillateam/

And lets see who wins out; lucid or precise  :)

And update

EDIT:  If you do not find it in sources.list.d; look here:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by siddi on 2012-12-11
I got this from the sources list

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse 
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse 
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse 
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse 
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

---

### Post by siddi on 2012-12-11
commented out mozilla team

iddharth@siddharth-Aspire-5570:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid InRelease                               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                          
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid InRelease                               
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security InRelease                      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates InRelease             
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main i386 Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid Release.gpg                             
Get:1 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security Release.gpg [198 B]          
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main TranslationIndex                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                     
Get:2 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates Release.gpg [198 B]           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages         
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner TranslationIndex                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:3 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security Release [57.3 kB]            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:4 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates Release [58.3 kB]             
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en_AU                
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en                   
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Sources                            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main i386 Packages                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted i386 Packages                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe i386 Packages                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse i386 Packages                
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main TranslationIndex                   
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse TranslationIndex             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted TranslationIndex             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe TranslationIndex               
Get:5 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Sources [133 kB]        
Get:6 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Sources [1,267 B] 
Get:7 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Sources [42.9 kB]   
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en_AU               
Get:8 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Sources [2,350 B] 
Get:9 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main i386 Packages [467 kB]  
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en                  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_AU             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:10 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted i386 Packages [2,867 B]
Get:11 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe i386 Packages [139 kB]
Get:12 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse i386 Packages [5,353 B]
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main TranslationIndex          
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse TranslationIndex    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted TranslationIndex    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe TranslationIndex      
Get:13 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main Sources [233 kB]        
Get:14 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted Sources [2,196 B] 
Get:15 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe Sources [105 kB]    
Get:16 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse Sources [5,827 B] 
Get:17 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main i386 Packages [664 kB]  
Get:18 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted i386 Packages [4,630 B]
Get:19 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe i386 Packages [285 kB]
Get:20 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse i386 Packages [11.5 kB]
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main TranslationIndex           
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse TranslationIndex     
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted TranslationIndex     
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe TranslationIndex       
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Translation-en_AU                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Translation-en_AU            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Translation-en_AU            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main Translation-en_AU          
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse Translation-en_AU    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted Translation-en_AU    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Translation-en                     
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Translation-en               
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Translation-en               
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Translation-en_AU              
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Translation-en                 
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Translation-en_AU         
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Translation-en            
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Translation-en_AU   
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Translation-en      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Translation-en_AU   
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Translation-en      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Translation-en_AU     
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Translation-en        
Fetched 2,221 kB in 49s (45.3 kB/s)                                            
Reading package lists... Done
N: Ignoring file 'Untitled Document 1' in directory '/etc/apt/sources.list.d/' as it has no filename extension
N: Ignoring file 'Untitled Document 2' in directory '/etc/apt/sources.list.d/' as it has no filename extension

---

### Post by siddi on 2012-12-11
**I can't get rid of the untitled document in the sources list... and the update manager stil gives the following error**

Could not initialize the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'W:Ignoring file 'Untitled Document 1' in directory '/etc/apt/sources.list.d/' as it has no filename extension, W:Ignoring file 'Untitled Document 2' in directory '/etc/apt/sources.list.d/' as it has no filename extension, W:Ignoring file 'Untitled Document 1' in directory '/etc/apt/sources.list.d/' as it has no filename extension, W:Ignoring file 'Untitled Document 2' in directory '/etc/apt/sources.list.d/' as it has no filename extension, E:The package update-manager needs to be reinstalled, but I can't find an archive for it


> **siddi said:**
> commented out mozilla team

iddharth@siddharth-Aspire-5570:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid InRelease                               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                          
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid InRelease                               
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security InRelease                      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates InRelease             
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main i386 Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid Release.gpg                             
Get:1 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security Release.gpg [198 B]          
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main TranslationIndex                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                     
Get:2 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates Release.gpg [198 B]           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages         
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner TranslationIndex                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:3 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security Release [57.3 kB]            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:4 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates Release [58.3 kB]             
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en_AU                
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en                   
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Sources                            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main i386 Packages                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted i386 Packages                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe i386 Packages                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse i386 Packages                
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main TranslationIndex                   
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse TranslationIndex             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted TranslationIndex             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe TranslationIndex               
Get:5 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Sources [133 kB]        
Get:6 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Sources [1,267 B] 
Get:7 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Sources [42.9 kB]   
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en_AU               
Get:8 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Sources [2,350 B] 
Get:9 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main i386 Packages [467 kB]  
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en                  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_AU             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:10 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted i386 Packages [2,867 B]
Get:11 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe i386 Packages [139 kB]
Get:12 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse i386 Packages [5,353 B]
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main TranslationIndex          
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse TranslationIndex    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted TranslationIndex    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe TranslationIndex      
Get:13 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main Sources [233 kB]        
Get:14 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted Sources [2,196 B] 
Get:15 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe Sources [105 kB]    
Get:16 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse Sources [5,827 B] 
Get:17 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main i386 Packages [664 kB]  
Get:18 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted i386 Packages [4,630 B]
Get:19 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe i386 Packages [285 kB]
Get:20 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse i386 Packages [11.5 kB]
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main TranslationIndex           
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse TranslationIndex     
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted TranslationIndex     
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe TranslationIndex       
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Translation-en_AU                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Translation-en_AU            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Translation-en_AU            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main Translation-en_AU          
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse Translation-en_AU    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted Translation-en_AU    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Translation-en                     
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Translation-en               
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Translation-en               
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Translation-en_AU              
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Translation-en                 
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Translation-en_AU         
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Translation-en            
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Translation-en_AU   
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Translation-en      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Translation-en_AU   
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Translation-en      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Translation-en_AU     
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Translation-en        
Fetched 2,221 kB in 49s (45.3 kB/s)                                            
Reading package lists... Done
N: Ignoring file 'Untitled Document 1' in directory '/etc/apt/sources.list.d/' as it has no filename extension
N: Ignoring file 'Untitled Document 2' in directory '/etc/apt/sources.list.d/' as it has no filename extension

---

### Post by ibjsb4 on 2012-12-11
First off.  You need to stop using "quote tags" when posting and start using "code tags".  Example:

```
iddharth@siddharth-Aspire-5570:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid InRelease                               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                          
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid InRelease                               
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security InRelease                      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates InRelease             
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main i386 Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid Release.gpg                             
Get:1 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security Release.gpg [198 B]          
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main TranslationIndex                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                     
Get:2 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates Release.gpg [198 B]           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner i386 Packages         
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner TranslationIndex                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:3 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security Release [57.3 kB]            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:4 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates Release [58.3 kB]             
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en_AU                
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en                   
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Sources                            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main i386 Packages                      
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted i386 Packages                
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe i386 Packages                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse i386 Packages                
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main TranslationIndex                   
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse TranslationIndex             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted TranslationIndex             
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe TranslationIndex               
Get:5 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Sources [133 kB]        
Get:6 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Sources [1,267 B] 
Get:7 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Sources [42.9 kB]   
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en_AU               
Get:8 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Sources [2,350 B] 
Get:9 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main i386 Packages [467 kB]  
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Translation-en                  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_AU             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:10 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted i386 Packages [2,867 B]
Get:11 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe i386 Packages [139 kB]
Get:12 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse i386 Packages [5,353 B]
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main TranslationIndex          
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse TranslationIndex    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted TranslationIndex    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe TranslationIndex      
Get:13 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main Sources [233 kB]        
Get:14 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted Sources [2,196 B] 
Get:15 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe Sources [105 kB]    
Get:16 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse Sources [5,827 B] 
Get:17 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main i386 Packages [664 kB]  
Get:18 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted i386 Packages [4,630 B]
Get:19 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe i386 Packages [285 kB]
Get:20 [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse i386 Packages [11.5 kB]
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main TranslationIndex           
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse TranslationIndex     
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted TranslationIndex     
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/universe TranslationIndex       
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Translation-en_AU                  
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Translation-en_AU            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Translation-en_AU            
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/main Translation-en_AU          
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/multiverse Translation-en_AU    
Hit [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-updates/restricted Translation-en_AU    
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/main Translation-en                     
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/multiverse Translation-en               
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/restricted Translation-en               
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Translation-en_AU              
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid/universe Translation-en                 
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Translation-en_AU         
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/main Translation-en            
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Translation-en_AU   
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/multiverse Translation-en      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Translation-en_AU   
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/restricted Translation-en      
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Translation-en_AU     
Ign [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) lucid-security/universe Translation-en        
Fetched 2,221 kB in 49s (45.3 kB/s)                                            
Reading package lists... Done
N: Ignoring file 'Untitled Document 1' in directory '/etc/apt/sources.list.d/' as it has no filename extension
N: Ignoring file 'Untitled Document 2' in directory '/etc/apt/sources.list.d/' as it has no filename extension
```

Here's how to do that.

[ATTACH]228567[/ATTACH]

Now please post the output of:

```
cat -n /etc/apt/sources.list.d/*
```

and
```

cat -n /etc/apt/sources.list.save
```

---

### Post by siddi on 2012-12-11
```
siddharth@siddharth-Aspire-5570:~$ cat -n /etc/apt/sources.list.d/*
     1    #deb http://ppa.launchpad.net/ailurus/ppa/ubuntu precise main
     2    #deb-src http://ppa.launchpad.net/ailurus/ppa/ubuntu precise main
     3    #deb http://ppa.launchpad.net/ailurus/ppa/ubuntu precise main
     4    #deb-src http://ppa.launchpad.net/ailurus/ppa/ubuntu precise main
     5    deb http://ppa.launchpad.net/ailurus/ppa/ubuntu precise main
     6    deb-src http://ppa.launchpad.net/ailurus/ppa/ubuntu precise main
     7    #deb http://ppa.launchpad.net/ailurus/ppa/ubuntu precise main
     8    #deb-src http://ppa.launchpad.net/ailurus/ppa/ubuntu precise main
     9    deb http://ppa.launchpad.net/ailurus/ppa/ubuntu precise main
    10    deb-src http://ppa.launchpad.net/ailurus/ppa/ubuntu precise main
    11    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
    12    # You may comment out this entry, but any other modifications may be lost.
    13    deb http://dl.google.com/linux/chrome/deb/ stable main
    14    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
    15    # You may comment out this entry, but any other modifications may be lost.
    16    deb http://dl.google.com/linux/chrome/deb/ stable main
    17    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
    18    # You may comment out this entry, but any other modifications may be lost.
    19    deb http://dl.google.com/linux/talkplugin/deb/ stable main
    20    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
    21    # You may comment out this entry, but any other modifications may be lost.
    22    deb http://dl.google.com/linux/talkplugin/deb/ stable main
    23    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
    24    # You may comment out this entry, but any other modifications may be lost.
    25    deb http://dl.google.com/linux/talkplugin/deb/ stable main
    26    deb http://download.ebz.epson.net/dsc/op/stable/debian/ lsb3.2 main
    27    deb http://download.ebz.epson.net/dsc/op/stable/debian/ lsb3.2 main
    28    #deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu precise main
    29    #deb-src http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu precise main
    30    deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu precise main
    31    deb-src http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu precise main
    32    deb http://archive.canonical.com/ubuntu precise partner #Added by software-center
    33    deb http://archive.canonical.com/ubuntu oneiric partner #Added by software-center
    34    deb http://archive.canonical.com/ubuntu precise partner #Added by software-center
    35    deb http://archive.canonical.com/ubuntu precise partner #Added by software-center
    36    deb http://archive.canonical.com/ubuntu precise partner #Added by software-center
    37    deb http://archive.canonical.com/ubuntu precise partner #Added by software-center


```

---

### Post by siddi on 2012-12-11
```
siddharth@siddharth-Aspire-5570:~$ cat -n /etc/apt/sources.list.save
     1    # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://au.archive.ubuntu.com/ubuntu/ precise main restricted
     6    deb-src http://au.archive.ubuntu.com/ubuntu/ precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    11    deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://au.archive.ubuntu.com/ubuntu/ precise universe
    17    deb-src http://au.archive.ubuntu.com/ubuntu/ precise universe
    18    deb http://au.archive.ubuntu.com/ubuntu/ precise-updates universe
    19    deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://au.archive.ubuntu.com/ubuntu/ precise multiverse
    27    deb-src http://au.archive.ubuntu.com/ubuntu/ precise multiverse
    28    deb http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    29    deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    37    deb-src http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    41    deb http://security.ubuntu.com/ubuntu precise-security universe
    42    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    43    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu oneiric partner
    51    # deb-src http://archive.canonical.com/ubuntu oneiric partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu precise main
    56    deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by ibjsb4 on 2012-12-12
OK, I finally got this figured out.

You did a version upgrade to 12.04, but it went wrong.
That shows in your backup sources list (sources.list.save).

You then tried going back to 10.04 by going to Ubuntu Sources List Generator ([http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)) and creating a new list.

When that did not work you posted (post #1):

[HTML]I have red danger message on my main toolbar and it says error: broken count>0

and it also says the installed packags have unmet dependancies

Further i am not able to run update manager cos it says 'this package is broken' and is asking me to disable third party repositories which i don;t know how to.

In the details it says the following packages have unmet dependancies.... but is blank below.

My facebook page is getting ads on top witth loud sounds and i think my ubuntu has downloaded unwanted stuff

Please help[/HTML]

---

### Post by siddi on 2012-12-12
Hi,
Thanks heaps... But what do i do now?

---

### Post by ibjsb4 on 2012-12-12
> **siddi said:**
> Hi,
Thanks heaps... But what do i do now?

It took 33 post for the facts to come out, thanks heaps to you too.

---

### Post by siddi on 2012-12-12
Do i have to reload the whole version? I am not very tech savvy.. I was trying all different codes i saw on the forums to get rid of the error on update manager and it progressively got worse and in the end the update manager and software center stopped working all together

Is there any solution ?

---

