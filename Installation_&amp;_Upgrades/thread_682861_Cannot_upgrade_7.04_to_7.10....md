---
title: "Cannot upgrade 7.04 to 7.10...?"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by chazdraves on 2008-01-30
Greetings! I'm afraid I've found a bit of a problem. I'm presently using Feisty Fawn with all the upgrades, but the Update Manager will not find the new distro. If I use the proper command at the root terminal, it too tells me there is no new distro available, yet my "About Ubuntu" clearly states that I'm using 7.04.

Help? I'm a lost newb in Linux, and as we all know, that's a rough deal.

- Chaz

---

### Post by zvacet on 2008-01-30
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by chazdraves on 2008-01-30
Nothing. 

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US    
Get:2 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]        
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages           
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US       
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release              
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Sources
Fetched 197B in 2s (73B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I tried going back into the Update Manager as well after that, but it still says "up-to-date".

Thanks,
_ Chaz

---

### Post by zvacet on 2008-01-31
```
cat /etc/apt/sources.list
```

It look like you have mixed source list.Post it here to fix it .

---

### Post by chazdraves on 2008-01-31
Thanks for the help guys, I ended up downloading the latest version and burning it to a disc. Strangely, even when I put the disc in, it didn't try to update. I finally moved everything important to my Windows partition and re-installed completely. Now everything works great and I even got my wireless internet working! (WiFi Radar)

I'm not sure what the problem was, but it seems it ran pretty deep.

Regards,
- Chaz

---

### Post by zvacet on 2008-01-31
> Strangely, even when I put the disc in, it didn't try to update.

Because you use Live CD  and you are able to upgrade only with alternate CD.I´m glad that everything is working for you now.

---

