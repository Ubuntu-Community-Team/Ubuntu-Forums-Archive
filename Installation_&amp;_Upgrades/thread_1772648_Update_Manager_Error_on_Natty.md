---
title: "Update Manager Error on Natty"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by janno92 on 2011-05-31
ok, im back to ask for help for the second time,

i am running on ubuntu 11.04, and to keep my system uptodate, i am randomly checking and installing updates, but this time it showed me error, see the screenshot

[IMG]http://oi52.tinypic.com/95sxnr.jpg[/IMG]

any inputs to solve this?i already checked (after googling) the canonical partner and canonical partner(source something) repositories under synaptic >settings>repos..
 and nothing happened,the error is still there..

---

### Post by tommcd on 2011-06-01
Are you using any third party repositories in your sources? This includes those all too problematic PPA repos. If so, then remove those and check again for updates. Be sure to reload your sources when prompted after removing any third party repos.
Also, for troubleshooting purposes, post the output of:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
from the terminal in code tags ```
 
``` so we can see what is going on here.
The symbol for the code tags is the # at the top of the post window.

---

### Post by janno92 on 2011-06-01
unchecking 3rd party repos didnt solve it..
okay heres the output of sudo at-get update

```
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://archive.canonical.com natty InRelease                               
Ign http://ph.archive.ubuntu.com natty InRelease                     
Ign http://ph.archive.ubuntu.com natty-updates InRelease             
Hit http://archive.canonical.com natty Release.gpg                   
Hit http://ph.archive.ubuntu.com natty Release.gpg                   
Hit http://archive.canonical.com natty Release                       
Get:1 http://security.ubuntu.com natty-security Release.gpg                    
Hit http://ph.archive.ubuntu.com natty-updates Release.gpg           
Hit http://archive.canonical.com natty/partner Sources               
Get:2 http://security.ubuntu.com natty-security Release              
Hit http://ph.archive.ubuntu.com natty Release                                 
Hit http://archive.canonical.com natty/partner i386 Packages                   
Hit http://ph.archive.ubuntu.com natty-updates Release                         
Ign http://archive.canonical.com natty/partner TranslationIndex                
Get:3 http://security.ubuntu.com natty-security/main Sources [9,242 B]         
Hit http://ph.archive.ubuntu.com natty/main Sources                            
Hit http://ph.archive.ubuntu.com natty/restricted Sources                      
Hit http://ph.archive.ubuntu.com natty/universe Sources                        
Hit http://ph.archive.ubuntu.com natty/multiverse Sources                      
Get:4 http://security.ubuntu.com natty-security/restricted Sources [14 B]      
Get:5 http://security.ubuntu.com natty-security/universe Sources [3,152 B]     
Get:6 http://security.ubuntu.com natty-security/multiverse Sources [647 B]     
Get:7 http://security.ubuntu.com natty-security/main i386 Packages [29.0 kB]   
Ign http://ppa.launchpad.net natty InRelease                                   
Get:8 http://security.ubuntu.com natty-security/restricted i386 Packages [14 B]
Ign http://ppa.launchpad.net natty InRelease                                   
Get:9 http://security.ubuntu.com natty-security/universe i386 Packages [11.6 kB]
Get:10 http://security.ubuntu.com natty-security/multiverse i386 Packages [2,071 B]
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://archive.canonical.com natty/partner Translation-en_PH               
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://ppa.launchpad.net natty InRelease                                   
Get:11 http://ppa.launchpad.net natty Release.gpg [316 B]            
Get:12 http://ppa.launchpad.net natty Release.gpg [316 B]                      
Get:13 http://ppa.launchpad.net natty Release.gpg [316 B]                      
Get:14 http://ppa.launchpad.net natty Release [9,762 B]              
Ign http://ppa.launchpad.net natty Release                                     
Get:15 http://ppa.launchpad.net natty Release [9,738 B]                        
Ign http://ppa.launchpad.net natty Release                                     
Hit http://ph.archive.ubuntu.com natty/main i386 Packages                      
Get:16 http://ppa.launchpad.net natty Release [9,744 B]              
Ign http://ppa.launchpad.net natty Release                                     
Hit http://ph.archive.ubuntu.com natty/restricted i386 Packages                
Ign http://ppa.launchpad.net natty/main Sources/DiffIndex            
Hit http://ph.archive.ubuntu.com natty/universe i386 Packages        
Ign http://ppa.launchpad.net natty/main i386 Packages/DiffIndex      
Hit http://ph.archive.ubuntu.com natty/multiverse i386 Packages      
Ign http://ppa.launchpad.net natty/main TranslationIndex             
Ign http://ph.archive.ubuntu.com natty/main TranslationIndex         
Ign http://ppa.launchpad.net natty/main Sources/DiffIndex            
Ign http://ph.archive.ubuntu.com natty/multiverse TranslationIndex   
Ign http://ppa.launchpad.net natty/main i386 Packages/DiffIndex      
Ign http://ph.archive.ubuntu.com natty/restricted TranslationIndex   
Ign http://ppa.launchpad.net natty/main TranslationIndex             
Ign http://ph.archive.ubuntu.com natty/universe TranslationIndex     
Ign http://ppa.launchpad.net natty/main Sources/DiffIndex            
Hit http://ph.archive.ubuntu.com natty-updates/main Sources          
Ign http://ppa.launchpad.net natty/main i386 Packages/DiffIndex      
Hit http://ph.archive.ubuntu.com natty-updates/restricted Sources    
Ign http://ppa.launchpad.net natty/main TranslationIndex             
Hit http://ph.archive.ubuntu.com natty-updates/universe Sources      
Hit http://ppa.launchpad.net natty/main Sources                      
Hit http://ph.archive.ubuntu.com natty-updates/multiverse Sources    
Hit http://ppa.launchpad.net natty/main i386 Packages                
Hit http://ph.archive.ubuntu.com natty-updates/main i386 Packages    
Hit http://ph.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://ph.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://ph.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://ph.archive.ubuntu.com natty-updates/main TranslationIndex 
Ign http://ph.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://ph.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://ph.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://security.ubuntu.com natty-security/main Translation-en_PH 
Ign http://security.ubuntu.com natty-security/main Translation-en    
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_PH
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_PH
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_PH
Ign http://security.ubuntu.com natty-security/universe Translation-en
Hit http://ppa.launchpad.net natty/main Sources                      
Hit http://ppa.launchpad.net natty/main i386 Packages
Hit http://ppa.launchpad.net natty/main Sources
Hit http://ppa.launchpad.net natty/main i386 Packages
Ign http://ph.archive.ubuntu.com natty/main Translation-en_PH
Ign http://ph.archive.ubuntu.com natty/main Translation-en
Ign http://ph.archive.ubuntu.com natty/multiverse Translation-en_PH
Ign http://ph.archive.ubuntu.com natty/multiverse Translation-en
Ign http://ph.archive.ubuntu.com natty/restricted Translation-en_PH
Ign http://ph.archive.ubuntu.com natty/restricted Translation-en
Ign http://ph.archive.ubuntu.com natty/universe Translation-en_PH
Ign http://ph.archive.ubuntu.com natty/universe Translation-en
Ign http://ph.archive.ubuntu.com natty-updates/main Translation-en_PH
Ign http://ph.archive.ubuntu.com natty-updates/main Translation-en
Ign http://ph.archive.ubuntu.com natty-updates/multiverse Translation-en_PH
Ign http://ph.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://ph.archive.ubuntu.com natty-updates/restricted Translation-en_PH
Ign http://ph.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://ph.archive.ubuntu.com natty-updates/universe Translation-en_PH
Ign http://ph.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_PH
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_PH
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_PH
Ign http://ppa.launchpad.net natty/main Translation-en
Fetched 84.0 kB in 49s (1,686 B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 610C90B170C398A2
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

```

---

### Post by ken78724 on 2011-06-01
upgrading from 10.10 to 11.04 on a 40 gig, the 'man - db' triggering processors failed to install. So I ask, Please advise me: amidst a 10.10 upgrade to 11.04 I received a "Could not install 'man-db'" after which the install died twice and now I cannot login. subprocess installed post-installation scripts. PC upgrade and analyzer said "error no space on device". Is interesting as on same PC with a 500 gig slave, it said the 17.2 gig set aside for install was insufficient to do operations. So, I unplugged the 500 gig and plugged in only the 40 gig and upgrading to 11.04 to salvage non-backed up files. On this 2nd HD I get the insufficient space notice. What am I being told? [i have 4 gig of ram]

truly would like to get the fast hardware on this PC to function as I want no fowl ups, preferably to bang out some DVDs and productions. Help me cut to the chase.

---

### Post by janno92 on 2011-06-01
^ ive got no idea.


will be marking this thread as solved, thank ya'll folks.

solved it by running 
```
sudo apt-get update sudo apt-get dist-upgrade 
```

---

### Post by tommcd on 2011-06-01
> **janno92 said:**
> 
will be marking this thread as solved, thank ya'll folks.
solved it by running 
sudo apt-get update sudo apt-get dist-upgrade 
Your output of *sudo apt-get update* still shows a lot of PPA stuff in there.
Are you still getting that when you check for updates?
Be sure you have removed all third party repos. If you feel you must use a boatload of potentially problematic third party repos, then you can try adding them back one at a time until you break something. This way, if something breaks, you will at least know what repo caused it.
I do not use third party repos myself.

---

### Post by kalyp on 2011-06-01
That solves it for now, but if you're having the same thing as me, you'll still have 
```
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
```
at the end when doing apt-get update, so you'll run into that problem again.
I found the solution here [http://doc.ubuntu-fr.org/apt-key](http://doc.ubuntu-fr.org/apt-key) (sorry French)
For the example above, just run
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 61E091672E206FF0
```
(looks like you need to do it for 3 different keys)

That solved it for me, now apt-get update doesn't generate any errors.

---

### Post by beemboy on 2013-04-19
If you have trouble running the above command because you are behind a firewall, then you can go straight to [http://keyserver.ubuntu.com/](http://keyserver.ubuntu.com/), search for your key (remember to put a '0x' in front of the hex identifier), save it to text and import it with apt-key.

See: [http://superuser.com/q/300865](http://superuser.com/q/300865)

---

### Post by wildmanne39 on 2013-04-19
Thread closed. Please do not post in old threads.

---

