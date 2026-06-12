---
title: "Why &quot;Ign&quot; all of a sudden?"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by Majorix on 2007-08-07
Why now all of a sudden when I try to update the repos I get Ign instead of Hit before the site name?

```
 sudo apt-get update
Get:1 http://archive.canonical.com feisty-commercial Release.gpg [191B]
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US      
Get:2 http://wine.budgetdedicated.com feisty Release.gpg [191B]                
Ign http://wine.budgetdedicated.com feisty/main Translation-en_US              
Get:3 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Get:4 http://packages.medibuntu.org feisty Release.gpg [189B]                  
Hit http://archive.canonical.com feisty-commercial Release                     
Hit http://wine.budgetdedicated.com feisty Release                             
Get:5 http://www.getautomatix.com feisty Release.gpg [189B]                    
Ign http://www.getautomatix.com feisty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Get:6 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B]         
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com feisty-backports/restricted Translation-en_US 
Ign http://packages.medibuntu.org feisty/free Translation-en_US                
Ign http://packages.medibuntu.org feisty/non-free Translation-en_US            
Hit http://archive.canonical.com feisty-commercial/main Packages               
Ign http://wine.budgetdedicated.com feisty/main Packages                       
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US   
Ign http://us.archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US   
Hit http://www.getautomatix.com feisty Release                                 
Hit http://wine.budgetdedicated.com feisty/main Sources                        
Get:7 http://us.archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-security/main Translation-en_US        
Ign http://us.archive.ubuntu.com feisty-security/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com feisty-security/universe Translation-en_US    
Ign http://us.archive.ubuntu.com feisty-security/multiverse Translation-en_US  
Hit http://wine.budgetdedicated.com feisty/main Packages                       
Hit http://www.getautomatix.com feisty/main Packages                 
Get:8 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US
Get:9 http://us.archive.ubuntu.com feisty-proposed Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-proposed/universe Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-backports Release
Hit http://us.archive.ubuntu.com feisty-security Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty-proposed Release
Hit http://packages.medibuntu.org feisty Release                    
Hit http://us.archive.ubuntu.com feisty/main Packages
Ign http://packages.medibuntu.org feisty/free Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Ign http://packages.medibuntu.org feisty/non-free Packages
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/restricted Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Sources
Hit http://us.archive.ubuntu.com feisty-backports/restricted Sources
Hit http://us.archive.ubuntu.com feisty-backports/universe Sources
Hit http://us.archive.ubuntu.com feisty-backports/multiverse Sources
Hit http://packages.medibuntu.org feisty/free Packages
Hit http://us.archive.ubuntu.com feisty-backports/main Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Hit http://us.archive.ubuntu.com feisty-security/main Packages
Hit http://packages.medibuntu.org feisty/non-free Packages
Hit http://us.archive.ubuntu.com feisty-security/restricted Packages
Hit http://us.archive.ubuntu.com feisty-security/main Sources
Hit http://us.archive.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty-security/universe Packages
Hit http://us.archive.ubuntu.com feisty-security/universe Sources
Hit http://us.archive.ubuntu.com feisty-security/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/universe Packages
Hit http://us.archive.ubuntu.com feisty-proposed/restricted Packages
Hit http://us.archive.ubuntu.com feisty-proposed/main Packages
Hit http://us.archive.ubuntu.com feisty-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-proposed/universe Packages
Fetched 197B in 4s (48B/s)
Reading package lists... Done

```

Help please :(

Thank you.

---

### Post by tbroderick on 2007-08-07
You should be fine. It's the Translation-en_US that is being Ign not the repo.

---

### Post by Majorix on 2007-08-07
> **tbroderick said:**
> You should be fine. It's the Translation-en_US that is being Ign not the repo.

Yeah most but I wouldn't say all:
```
Ign http://packages.medibuntu.org feisty/free Packages
```
```
Ign http://packages.medibuntu.org feisty/non-free Packages
```

Anyone thinks why this could be happening?

---

### Post by tbroderick on 2007-08-07
> **Majorix said:**
> Yeah most but I wouldn't say all:
```
Ign http://packages.medibuntu.org feisty/free Packages
```
```
Ign http://packages.medibuntu.org feisty/non-free Packages
```

Anyone thinks why this could be happening?

Do you have them in there twice. Cause I see an Ign and a Hit for both.
```


Hit http://packages.medibuntu.org feisty/free Packages
Ign http://packages.medibuntu.org feisty/free Packages

Hit http://packages.medibuntu.org feisty/non-free Packages
Ign http://packages.medibuntu.org feisty/non-free Packages

```

---

### Post by Majorix on 2007-08-07
Just checked my sources.list and no I don't have it twice.

---

### Post by Majorix on 2007-08-08
Anybody?

---

### Post by Majorix on 2007-08-09
Any help? I am stuck :(

---

### Post by retr0virus on 2007-08-09
Well, I think I have the same problem.
I cannot update my system because everything fails like this:
```

retr0virus@vyrion:~$ sudo apt-get update
Ign http://wine.budgetdedicated.com feisty Release.gpg
Ign http://wine.budgetdedicated.com feisty/main Translation-de
Ign http://wine.budgetdedicated.com feisty Release
Ign http://wine.budgetdedicated.com feisty/main Packages
Ign http://wine.budgetdedicated.com feisty/main Sources
Fehl http://wine.budgetdedicated.com feisty/main Packages
  503 Connect failed
Fehl http://wine.budgetdedicated.com feisty/main Sources
  503 Connect failed
Ign http://security.ubuntu.com feisty-security Release.gpg
Ign http://security.ubuntu.com feisty-security/main Translation-de
Ign http://security.ubuntu.com feisty-security/restricted Translation-de
Ign http://security.ubuntu.com feisty-security/universe Translation-de
Ign http://security.ubuntu.com feisty-security/multiverse Translation-de
Ign http://archive.ubuntu.com feisty-updates Release.gpg
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-de
Ign http://archive.ubuntu.com feisty-updates/main Translation-de
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-de
Ign http://archive.ubuntu.com feisty-updates/universe Translation-de
Ign http://archive.canonical.com feisty-commercial Release.gpg
Ign http://archive.canonical.com feisty-commercial/main Translation-de
Ign http://ubuntu.geole.info feisty Release.gpg
Ign http://ubuntu.geole.info feisty/universe Translation-de
Ign http://ubuntu.geole.info feisty/multiverse Translation-de
Ign http://archive.ubuntu.com feisty-updates Release
Ign http://archive.canonical.com feisty-commercial Release
Ign http://ubuntu.geole.info feisty Release
Ign http://archive.ubuntu.com feisty-updates/restricted Packages
Ign http://archive.canonical.com feisty-commercial/main Packages
Ign http://ubuntu.geole.info feisty/universe Packages
Ign http://de.archive.ubuntu.com feisty Release.gpg
Ign http://de.archive.ubuntu.com feisty/main Translation-de
Ign http://de.archive.ubuntu.com feisty/restricted Translation-de
Ign http://de.archive.ubuntu.com feisty/universe Translation-de
Ign http://de.archive.ubuntu.com feisty/multiverse Translation-de
Ign http://de.archive.ubuntu.com feisty-updates Release.gpg
Ign http://de.archive.ubuntu.com feisty-updates/main Translation-de
Ign http://de.archive.ubuntu.com feisty-updates/restricted Translation-de
Ign http://security.ubuntu.com feisty-security Release
Ign http://medibuntu.sos-sts.com feisty Release.gpg
Ign http://medibuntu.sos-sts.com feisty/free Translation-de
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-de
Ign http://archive.ubuntu.com feisty-updates/main Packages
Ign http://archive.ubuntu.com feisty-updates/multiverse Packages
Ign http://archive.ubuntu.com feisty-updates/universe Packages
Fehl http://archive.canonical.com feisty-commercial/main Packages
  503 Connect failed
Ign http://ubuntu.geole.info feisty/multiverse Packages
Ign http://medibuntu.sos-sts.com feisty Release
Fehl http://archive.ubuntu.com feisty-updates/restricted Packages
  503 Connect failed
Fehl http://archive.ubuntu.com feisty-updates/main Packages
  503 Connect failed
Fehl http://archive.ubuntu.com feisty-updates/multiverse Packages
  503 Connect failed
Fehl http://ubuntu.geole.info feisty/universe Packages
  503 Connect failed
Ign http://medibuntu.sos-sts.com feisty/free Packages
Fehl http://archive.ubuntu.com feisty-updates/universe Packages
  503 Connect failed
Fehl http://ubuntu.geole.info feisty/multiverse Packages
  503 Connect failed
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Ign http://medibuntu.sos-sts.com feisty/free Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Sources
Fehl http://medibuntu.sos-sts.com feisty/free Packages
  503 Connect failed
Fehl http://medibuntu.sos-sts.com feisty/non-free Packages
  503 Connect failed
Fehl http://medibuntu.sos-sts.com feisty/free Sources
  503 Connect failed
Fehl http://medibuntu.sos-sts.com feisty/non-free Sources
  503 Connect failed
Ign http://security.ubuntu.com feisty-security/main Packages
Ign http://security.ubuntu.com feisty-security/restricted Packages
Ign http://security.ubuntu.com feisty-security/main Sources
Ign http://security.ubuntu.com feisty-security/restricted Sources
Ign http://security.ubuntu.com feisty-security/universe Packages
Ign http://security.ubuntu.com feisty-security/universe Sources
Ign http://security.ubuntu.com feisty-security/multiverse Packages
Ign http://security.ubuntu.com feisty-security/multiverse Sources
Fehl http://security.ubuntu.com feisty-security/main Packages
  503 Connect failed
Fehl http://security.ubuntu.com feisty-security/restricted Packages
  503 Connect failed
Fehl http://security.ubuntu.com feisty-security/main Sources
  503 Connect failed
Fehl http://security.ubuntu.com feisty-security/restricted Sources
  503 Connect failed
Fehl http://security.ubuntu.com feisty-security/universe Packages
  503 Connect failed
Fehl http://security.ubuntu.com feisty-security/universe Sources
  503 Connect failed
Fehl http://security.ubuntu.com feisty-security/multiverse Packages
  503 Connect failed
Fehl http://security.ubuntu.com feisty-security/multiverse Sources
  503 Connect failed
Ign http://de.archive.ubuntu.com feisty Release
Ign http://de.archive.ubuntu.com feisty-updates Release
Ign http://de.archive.ubuntu.com feisty/main Packages
Ign http://de.archive.ubuntu.com feisty/restricted Packages
Ign http://de.archive.ubuntu.com feisty/main Sources
Ign http://de.archive.ubuntu.com feisty/restricted Sources
Ign http://de.archive.ubuntu.com feisty/universe Packages
Ign http://de.archive.ubuntu.com feisty/universe Sources
Ign http://de.archive.ubuntu.com feisty/multiverse Packages
Ign http://de.archive.ubuntu.com feisty/multiverse Sources
Ign http://de.archive.ubuntu.com feisty-updates/main Packages
Ign http://de.archive.ubuntu.com feisty-updates/restricted Packages
Ign http://de.archive.ubuntu.com feisty-updates/main Sources
Ign http://de.archive.ubuntu.com feisty-updates/restricted Sources
Fehl http://de.archive.ubuntu.com feisty/main Packages
  503 Connect failed
Fehl http://de.archive.ubuntu.com feisty/restricted Packages
  503 Connect failed
Fehl http://de.archive.ubuntu.com feisty/main Sources
  503 Connect failed
Fehl http://de.archive.ubuntu.com feisty/restricted Sources
  503 Connect failed
Fehl http://de.archive.ubuntu.com feisty/universe Packages
  503 Connect failed
Fehl http://de.archive.ubuntu.com feisty/universe Sources
  503 Connect failed
Fehl http://de.archive.ubuntu.com feisty/multiverse Packages
  503 Connect failed
Fehl http://de.archive.ubuntu.com feisty/multiverse Sources
  503 Connect failed
Fehl http://de.archive.ubuntu.com feisty-updates/main Packages
  503 Connect failed
Fehl http://de.archive.ubuntu.com feisty-updates/restricted Packages
  503 Connect failed
Fehl http://de.archive.ubuntu.com feisty-updates/main Sources
  503 Connect failed
Fehl http://de.archive.ubuntu.com feisty-updates/restricted Sources
  503 Connect failed
Konnte http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://wine.budgetdedicated.com/apt/dists/feisty/main/source/Sources.gz nicht holen  503 Connect failed
Konnte http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://ubuntu.geole.info/dists/feisty/universe/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://ubuntu.geole.info/dists/feisty/multiverse/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz nicht holen  503 Connect failed
Konnte http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz nicht holen  503 Connect failed
Konnte http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz nicht holen  503 Connect failed
Konnte http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz nicht holen  503 Connect failed
Konnte http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz nicht holen  503 Connect failed
Konnte http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz nicht holen  503 Connect failed
Konnte http://de.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz nicht holen  503 Connect failed
Paketlisten werden gelesen... Fertig
E: Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt.

```
I can browse the internet and access to the servers without problems, but apt-get, aptitude and synaptic cannot connect to them.
I do not know what to do now. :(

---

### Post by forestpixie on 2007-08-09
I don't know if this'll help at all - 

[http://www.webservertalk.com/archive291-2006-2-1394937.html](http://www.webservertalk.com/archive291-2006-2-1394937.html)

I've looked at mine to see if I have anything in /var/lib/apt/lists/partial/ as the thread suggests and I don't - maybe you have?

Have you tried a different server - sort of guesed you might of but...

---

### Post by forestpixie on 2007-08-09
I get some "Ign" - but still seem to be able to access the repos - just tried to install my w32codecs again - and they don't need updating

---

### Post by retr0virus on 2007-08-09
Ok, it was my fault.
It seems that somehow the "direct internet connection" option was changed into a "proxy connection". Don't know why, but  I think it has something to do with my TOR installation.
Now it works again.

---

