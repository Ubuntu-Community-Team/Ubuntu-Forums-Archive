---
title: "Ubuntu software center - no connection"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by gilk on 2012-01-03
I get for any package I wish to install the error: failed to download package files check your Internet connection.
I have no connection problems (see this post?), and still, I get the same error on and on. rebooted the comp a few times, tried next day... no change...:-(
 TIA 
Gil

---

### Post by matt_symes on 2012-01-03
Hi

Open a terminal and type 

```
sudo apt-get update
```

Enter your password. It will not be echoed to the screen.

Post the results back here.

Kind regards

---

### Post by gilk on 2012-01-03
gilk@gilk-laptop:~$ sudo apt-get update
[sudo] password for gilk: 
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric InRelease
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Get:1 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric Release.gpg [198 B]                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates Release.gpg                   
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates Release                       
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Get:5 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]               
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric Release     
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/main Sources/DiffIndex       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                        
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/restricted Sources/DiffIndex 
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/universe Sources/DiffIndex   
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/multiverse Sources/DiffIndex 
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex 
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex      
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex    
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources/DiffIndex                    
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/main i386 Packages                    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
  
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/multiverse Translation-en             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Get:6 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Get:7 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US               
Get:8 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,214 B]       
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                      
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en             
Get:9 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [765 B]
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Fetched 5,655 B in 5s (1,002 B/s)
Reading package lists... Done
W: GPG error: [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG B2DFD25316B94077 Launchpad Cardápio unstable
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by matt_symes on 2012-01-03
Hi

You have some corrupted signatures.

Open a terminal and type

```
sudo apt-get clean
```

Enter your password as before.  Then type (or copy and paste)

```
sudo mv /var/lib/apt/lists{old}
```

```
sudo mkdir /var/lib/apt/lists
```

```
sudo apt-get update
```

Then try to use software center again.

It it works

```
sudo rm -rf /var/lib/apt/listsold
```

Kind regards

---

### Post by gilk on 2012-01-07
1. THANKS
2. Tried to do it, but after the second command, got the response:
gilk@gilk-laptop:~$ sudo apt-get clean
gilk@gilk-laptop:~$ sudo mv /var/lib/apt/lists{old}
[COLOR=SeaGreen]mv: missing destination file operand after `/var/lib/apt/lists{old}'
Try `mv --help' for more information.[/COLOR]

I think I need to make some change with the {old} ?!

---

### Post by bluexrider on 2012-01-07
> **gilk said:**
> I get for any package I wish to install the error: failed to download package files check your Internet connection.
I have no connection problems (see this post?), and still, I get the same error on and on. rebooted the comp a few times, tried next day... no change...:-(
 TIA 
Gil

I would suggest using a different server. 
Open 'software sources' go to 'Download from: Main Server' and change it to 'other' then choose 'best server' wait a few moments and close.

open terminal ```
sudo apt-get update && sudo apt-get upgrade 
```

---

### Post by gilk on 2012-01-07
> **bluexrider said:**
> I would suggest using a different server. 
Open 'software sources' go to 'Download from: Main Server' and change it to 'other' then choose 'best server' wait a few moments and close.

open terminal ```
sudo apt-get update && sudo apt-get upgrade 
```

THANKS!!!
It worked!

it chose as best server - Nepal (and I'm in the middle east - Israel...) and it worked.
Thanks matt_symes and bluexrider.

---

### Post by bluexrider on 2012-01-07
Good Job! Glad to help.
Please mark this 
(SOLVED)

---

### Post by leesh2405 on 2012-02-17
> **gilk said:**
> THANKS!!!
It worked!

it chose as best server - Nepal (and I'm in the middle east - Israel...) and it worked.
Thanks matt_symes and bluexrider.


Think you Too...:D

---

