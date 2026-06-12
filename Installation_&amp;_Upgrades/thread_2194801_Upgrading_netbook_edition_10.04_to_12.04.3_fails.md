---
title: "Upgrading netbook edition 10.04 to 12.04.3 fails"
date: 2013-12-20
forum: Installation &amp; Upgrades
---

### Post by gslepic on 2013-12-20
Hi i was ignoring upgrade of my ubuntu ffor quite a time.
now when i finaly decided to give it a try, it does not complete with message: 

B&#283;hem plánování povýšení systému nastal ne&#345;ešitelný 
problém: 
E:Unable to correct problems, you have held broken packages. 


Možné p&#345;í&#269;iny: 
* Povyšování na p&#345;edproduk&#269;ní verzi Ubuntu 
* Spušt&#283;ný systém je p&#345;edproduk&#269;ní verze Ubuntu 
* V systému jsou neoficiální softwarové balí&#269;ky neposkytované 
od Ubuntu 


Pokud nic z toho nepom&#367;že, nahlaste prosím tento problém pomocí 
p&#345;íkazu 'ubuntu-bug update-manager'. 

I am sorry it is in czech, ill try to translate:

During upgrade an unsolvable problem has occured:
E:Unable to correct problems, you have held broken packages. 
Possible causes:
* Upgrading to pre-production version
* Current system is pre-production version
* There are inofficial packages not by Ubuntu

If none of that helps try bla bla bla...

I am almost sure i have removed all third party packages, but the upgrade process still end in the same point

any help?

---

### Post by mörgæs on 2013-12-20
Hi, welcome to the fora.

First of all I wouldn't recommend upgrades, always a fresh install.

Let's begin with the commands

```
sudo apt-get update
sudo apt-get -f install
```

Please run and post the output in CODE tags. Don't report the bug against update manager.

---

### Post by gslepic on 2013-12-21
```
$sudo apt-get update
Cíl http://archive.ubuntu.com lucid Release.gpg
Cíl http://archive.ubuntu.com/ubuntu/ lucid/main Translation-cs
Cíl http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-cs
Cíl http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-cs
Cíl http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-cs
Mám:1 http://archive.ubuntu.com lucid-updates Release.gpg [198B]
Cíl http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-cs
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-cs
Cíl http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-cs
Cíl http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-cs
Mám:2 http://archive.ubuntu.com lucid-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-cs
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-cs
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-cs
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-cs
Cíl http://archive.ubuntu.com lucid Release
Mám:3 http://archive.ubuntu.com lucid-updates Release [58,3kB]
Mám:4 http://archive.ubuntu.com lucid-security Release [57,3kB]
Cíl http://archive.ubuntu.com lucid/main Packages    
Cíl http://archive.ubuntu.com lucid/restricted Packages
Cíl http://archive.ubuntu.com lucid/main Sources  
Cíl http://archive.ubuntu.com lucid/restricted Sources
Cíl http://archive.ubuntu.com lucid/universe Packages
Cíl http://archive.ubuntu.com lucid/universe Sources
Cíl http://archive.ubuntu.com lucid/multiverse Packages
Cíl http://archive.ubuntu.com lucid/multiverse Sources
Mám:5 http://archive.ubuntu.com lucid-updates/main Packages [729kB]
Mám:6 http://archive.ubuntu.com lucid-updates/restricted Packages [4 630B]
Mám:7 http://archive.ubuntu.com lucid-updates/main Sources [334kB]
Mám:8 http://archive.ubuntu.com lucid-updates/restricted Sources [2 196B]
Mám:9 http://archive.ubuntu.com lucid-updates/universe Packages [295kB]
Mám:10 http://archive.ubuntu.com lucid-updates/universe Sources [110kB]                                                                                                
Mám:11 http://archive.ubuntu.com lucid-updates/multiverse Packages [11,5kB]                                                                                            
Mám:12 http://archive.ubuntu.com lucid-updates/multiverse Sources [5 817B]                                                                                             
Mám:13 http://archive.ubuntu.com lucid-security/main Packages [530kB]                                                                                                  
Mám:14 http://archive.ubuntu.com lucid-security/restricted Packages [2 867B]                                                                                           
Mám:15 http://archive.ubuntu.com lucid-security/main Sources [240kB]                                                                                                   
Mám:16 http://archive.ubuntu.com lucid-security/restricted Sources [1 267B]                                                                                            
Mám:17 http://archive.ubuntu.com lucid-security/universe Packages [148kB]                                                                                              
Mám:18 http://archive.ubuntu.com lucid-security/universe Sources [46,6kB]                                                                                              
Mám:19 http://archive.ubuntu.com lucid-security/multiverse Packages [5 366B]                                                                                           
Mám:20 http://archive.ubuntu.com lucid-security/multiverse Sources [2 347B]                                                                                            
Staženo 2 584kB za 12s (200kB/s)                                                                                                                                       
&#268;tu seznamy balík&#367;... Hotovo

```

```
$ sudo apt-get -f install
&#268;tu seznamy balík&#367;... Hotovo
Vytvá&#345;ím strom závislostí       
&#268;tu stavové informace... Hotovo
0 aktualizováno, 0 nov&#283; instalováno, 0 k odstran&#283;ní a 0 neaktualizováno.

```

> First of all I wouldn't recommend upgrades, always a fresh install.
Why wouldnt you? i was also thinking about that but i dont wanna loose my customizations..

---

### Post by mörgæs on 2013-12-21
Because, as you see, they tend to be more troublesome than a fresh install, even if you have to configure the system after install. More info in the link in my signature.

Your system is still in 10.04-state, so no upgrade has been performed until now.

---

