---
title: "sudo apt-get upgrade concerns...."
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by ebozzz on 2007-04-11
When I run 

```
sudo apt-get upgrade
``` 

from the terminal on one of my machines all I get is the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

This only happens on one of my boxes. The output on the others after running the same command is a **LOT** more. The situation does not effect my upgrades when using Synaptic or the graphical tool for apt-get. Should I be worried?

---

### Post by zvacet on 2007-04-12
Are the repositories same in all your comps?Look in sources list,maybe something is commented and you don´t get updates from commented sources.

---

### Post by ebozzz on 2007-04-12
Thanks for the reply. Some of the apps are different but the OS is the same on all. I will check the source list to see it there is a difference.

---

### Post by Snowin on 2007-04-12
> **ebozzz said:**
> Thanks for the reply. Some of the apps are different but the OS is the same on all. I will check the source list to see it there is a difference.

APT is very intelligent.  If you don't need an update, it won't install it. It could be perfectly normal for two machines to require different updates if they aren't identical. As already mentioned it's still probably worth checking the repositories on both machines for inconsistencies though, provided they are both the same version of Ubuntu.

---

### Post by ebozzz on 2007-04-12
I don't think that you understand. I can run that command and get nothing then go to Synaptic and there are lots of packages to download. It's a problem from the CLI with this specific machine.

---

### Post by zvacet on 2007-04-13
Maybe just try this
```
sudo aptitude install apt
```

and after that

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by ebozzz on 2007-04-14
Thanks for the reply. There was no change after running your suggestion but I do appreciate your effort. :) 


```
*******@Fusion-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Automatic updates work fine. Manual updates through Synaptic and the Add/Remove Program application work fine. I just thought of something. The machine in question has 64 bit OS. All of the others are running on 32 bit. Maybe that has some bearing on the issue? Lots of free time for me tomorrow. That's when I will try to get a closer look at the source code.

---

### Post by ebozzz on 2007-04-15
Well, looking at the sourcelist is a moot point now. I am using Feisty 7.04 on this machine and have been receiving **lots** of updates. After receiving one on yesterday I was required to reboot. Everything appeared to be going well but the boot process hung at the splash screen. After a while it timed out and gave me an error related to my initramfs. I wasn't totally comfortable with attempting to fix the problem so I just did a re-install. Now I get my typical output after running the command. 

```
Get:1 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Get:3 http://medibuntu.sos-sts.com feisty Release.gpg [189B]                   
Get:4 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Hit http://archive.ubuntu.com feisty-backports Release                         
Hit http://security.ubuntu.com feisty-security Release                         
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US  
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:5 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Hit http://us.archive.ubuntu.com feisty Release                                
Hit http://archive.ubuntu.com feisty-backports/restricted Packages             
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://archive.ubuntu.com feisty-backports/main Packages                   
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages             
Hit http://archive.ubuntu.com feisty-backports/universe Packages               
Hit http://us.archive.ubuntu.com feisty/main Packages                          
Hit http://us.archive.ubuntu.com feisty/restricted Packages          
Hit http://us.archive.ubuntu.com feisty/main Sources                 
Hit http://security.ubuntu.com feisty-security/restricted Packages   
Hit http://security.ubuntu.com feisty-security/main Sources          
Hit http://security.ubuntu.com feisty-security/restricted Sources    
Hit http://us.archive.ubuntu.com feisty/restricted Sources           
Hit http://us.archive.ubuntu.com feisty/universe Packages            
Hit http://us.archive.ubuntu.com feisty/universe Sources             
Hit http://us.archive.ubuntu.com feisty/multiverse Packages          
Hit http://us.archive.ubuntu.com feisty/multiverse Sources           
Hit http://security.ubuntu.com feisty-security/universe Packages     
Hit http://security.ubuntu.com feisty-security/universe Sources      
Hit http://security.ubuntu.com feisty-security/multiverse Packages   
Hit http://security.ubuntu.com feisty-security/multiverse Sources    
Hit http://us.archive.ubuntu.com feisty-updates/main Packages        
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_US
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_US
Hit http://medibuntu.sos-sts.com feisty Release
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://medibuntu.sos-sts.com feisty/non-free Packages
Hit http://medibuntu.sos-sts.com feisty/free Sources
Hit http://medibuntu.sos-sts.com feisty/non-free Sources
Fetched 5B in 4s (1B/s)  
Reading package lists... Done
```  

The only thing that I can surmise is that some breakage occurred when I upgraded using the following command:

```
gksu "update-manager -c -d"
```

So I am back up and running better than ever. :)

---

