---
title: "Problem occured when checking for update in ubuntu 8.04"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by tusherr on 2008-11-11
Hello everybody, :mad:

I was trying to update ubuntu 8.04 by placing some packages in the /var/cache/apt/arcive/  directory. At that time I was changing something in the System-> preferences -> "Software sources". I unchecked all the sources there. But now I connect my PC with the internet and trying to update in from the internet but the update button getting red (error button) and shows an notification that "problem occured while checking for update." 
**How can I solve this problem**. 

-- Is there any text file in Ubuntu where I can change the flag variable so that those sources getting enable again? :confused:
-- My "synaptic package manager" also does not work. is there any alternative way to enable it? :confused:

PLEASE HELP ME. I NEED TO UPDATE UBUNTU 8.04 TO 8.10. :mad:

2sir
Bangladesh

---

### Post by taurus on 2008-11-11
If you have synaptic package manager or update-manager running, close it.  Then, open a terminal and post the outputs of these two commands.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Partyboi2 on 2008-11-11
Have you gone back to Software Sources and ticked the boxes you unticked? 
Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
sudo apt-get update
```

---

### Post by Ter Rymon on 2008-12-08
I have similar problem installing software using add/remove programs.
When finished program "planet penguin racer" installed would change screen resolution and then shut off and lock mouse in middle of screen.  Cannot uninstall using add/remove OR synaptic because both apps close as soon as they open.

sudo apt-get update produces the following:

```
terrymon@T-Ubuntu:~$ sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US          
Hit http://archive.canonical.com hardy Release                                 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US      
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com hardy-security Release                         
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://security.ubuntu.com hardy-security/main Packages                   
Hit http://archive.canonical.com hardy/partner Sources                        
Hit http://security.ubuntu.com hardy-security/restricted Packages             
Hit http://security.ubuntu.com hardy-security/main Sources                    
Hit http://security.ubuntu.com hardy-security/restricted Sources              
Hit http://security.ubuntu.com hardy-security/universe Packages               
Hit http://security.ubuntu.com hardy-security/universe Sources                
Hit http://security.ubuntu.com hardy-security/multiverse Packages             
Hit http://security.ubuntu.com hardy-security/multiverse Sources              
Hit http://us.archive.ubuntu.com hardy Release.gpg                            
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Segmentation faultsts... 0%

```

---

### Post by Ter Rymon on 2008-12-08
UPDATE: Forced to start new session which fixed problem, I was then able to get Synaptic to remove "ppracer" which then allowed Add/remove to finish loading as it would lock up while loading dependencies.

??? There may be a bug in the packages or in the way add/remove installed them???

Will not try repeating it, my kids[ or me] don't need to be playing more games anyway.

Thanks...

---

