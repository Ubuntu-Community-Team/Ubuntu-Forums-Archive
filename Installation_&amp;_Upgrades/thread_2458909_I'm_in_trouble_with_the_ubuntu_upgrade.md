---
title: "I'm in trouble with the ubuntu upgrade"
date: 2021-03-06
forum: Installation &amp; Upgrades
---

### Post by cereale979 on 2021-03-06
Hi all!!!!
I'm a newbie and i'm approached Ubuntu for my plex server because in windows environment i've got a ransonware and wasted all my precious films.... After that disaster i've chosen to migrate to Ubuntu, but when I try to upgrade the system, somethings goes wrong and i'm stuck to this version:

```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 19.10
Release:	19.10
Codename:	eoan

```

When I try to upgrade Ubuntu from Software Update, the 20.04 Focal fossa starts, I click on "Upgrade", and the procedures stucks at first step, and nothing appears... Could you please help me to made my system up to date?
I don't know why i'm in this situation, but I need to upgrade my system.
Thanks in advance.

Please, remember I'm a newbie!!!!:rolleyes::rolleyes:

---

### Post by howefield on 2021-03-06
19.10 isn't the version to use given it has reached End of Life. Probably better to clean install 20.04.2 which has a bit more than 4 years of support left.

---

### Post by cereale979 on 2021-03-06
Yes, I know. But i've this version and a plex server full of items... It's possible to upgrade this version to focal fossa?

---

### Post by ActionParsnip on 2021-03-06
If you run
```

sudo do-release-upgrade

```
Is it OK? If not then please give the full output. You can upgrade to 20.04 from 19.10 so a reinstall isn't required.

---

### Post by CelticWarrior on 2021-03-06
> **ActionParsnip said:**
> You can upgrade to 20.04 from 19.10 so a reinstall isn't required.

Yes and no.
19.10 is EoL already. The method is different than a release upgrade within the proper time to do it:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by grahammechanical on 2021-03-06
When a Ubuntu release reaches End of Life its repositories or sources are moved to a new location and that is old-releases.ubuntu.com/ubuntu/

You need to edit a file found at etc/apt/sources.list. You will need to be root to edit that text file. Lines prefixed by a # are comments and can be left alone. Lines like this one have to be changed

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) eoan multiverse

to something like

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) eoan multiverse

After saving that file you should be able to run

```
sudo apt update
sudo apt upgrade
```

then

```
sudo do-release-upgrade
```

should trigger the upgrade.

Regards

---

### Post by cereale979 on 2021-03-07
> **grahammechanical said:**
> When a Ubuntu release reaches End of Life its repositories or sources are moved to a new location and that is old-releases.ubuntu.com/ubuntu/

You need to edit a file found at etc/apt/sources.list. You will need to be root to edit that text file. Lines prefixed by a # are comments and can be left alone. Lines like this one have to be changed



to something like



After saving that file you should be able to run

```
sudo apt update
sudo apt upgrade
```

then

```
sudo do-release-upgrade
```

should trigger the upgrade.

Regards


Thank for all your help, but I'm stuck in trouble. Yes, I know, the script attached is in italian, I don't know how to change default language to made one in english, but I hope you'll find the problem also if it's in italian...

I've made the changes requested , but something goes wrong...

```

root@LHS3200:/etc/apt# sudo apt-get upgrade
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Calcolo dell'aggiornamento... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
root@LHS3200:/etc/apt# sudo do-release-upgrade
Verifica un nuovo rilascio di ubuntu
Il rilascio di Ubuntu in uso non è più supportato.
ERROR:root:incorrect translation for message 'For upgrade information, please visit:
%(url)s
' to 'Per informazioni sull'avanzamento consultare:
$(url)s
' (wrong number of arguments)
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife


Scaricamento di:1 Firma dello strumento di avanzamento versione [1.554 B]      
Scaricamento di:2 Strumento di avanzamento versione [1.341 kB]                 
Recuperati 1.343 kB in 0s (0 B/s)                                              
autenticazione di «focal.tar.gz» con «focal.tar.gz.gpg» 
estrazione di «focal.tar.gz»


Lettura della cache


Controllo gestore dei pacchetti
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze        
Lettura informazioni sullo stato... Fatto 
Trovato http://old-releases.ubuntu.com/ubuntu eoan InRelease                   
Trovato http://old-releases.ubuntu.com/ubuntu eoan-security InRelease          
Trovato http://old-releases.ubuntu.com/ubuntu eoan-updates InRelease           
Recuperati 0 B in 0s (0 B/s)                                                   
Lettura elenco dei pacchetti... Fatto     
Generazione albero delle dipendenze        
Lettura informazioni sullo stato... Fatto 


Ripristino dello stato originale del sistema


Interruzione
Lettura elenco dei pacchetti... Fatto     
Generazione albero delle dipendenze        
Lettura informazioni sullo stato... Fatto 
root@LHS3200:/etc/apt# 



```

with nano I've quoted all the previous dev and leaved only the old one... It's correct?

---

### Post by Impavidus on 2021-03-07
To change language from the localised version to the default, prefix the command with **LANG=C** . You can make it permament (somewhat) using```
export LANG=C
```Then all further commands you run in that terminal will give output in English. And if you're root already, there's no need for sudo.

---

### Post by cereale979 on 2021-03-07
```

root@LHS3200:/home/cereale979# LANG=C apt-get update
Hit:1 http://old-releases.ubuntu.com/ubuntu eoan InRelease
Hit:2 http://old-releases.ubuntu.com/ubuntu eoan-security InRelease
Hit:3 http://old-releases.ubuntu.com/ubuntu eoan-updates InRelease
Reading package lists... Done
root@LHS3200:/home/cereale979# LANG=C apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@LHS3200:/home/cereale979# LANG=C do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife


Get:1 Upgrade tool signature [1554 B]                                          
Get:2 Upgrade tool [1341 kB]                                                   
Fetched 1343 kB in 0s (0 B/s)                                                  
authenticate 'focal.tar.gz' against 'focal.tar.gz.gpg' 
extracting 'focal.tar.gz'


Reading cache


Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Hit http://old-releases.ubuntu.com/ubuntu eoan InRelease                       
Hit http://old-releases.ubuntu.com/ubuntu eoan-security InRelease              
Hit http://old-releases.ubuntu.com/ubuntu eoan-updates InRelease               
Fetched 0 B in 0s (0 B/s)                                                      
Reading package lists... Done    
Building dependency tree          
Reading state information... Done


Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done



```

Now in english but ever in trouble.... Where is located the upgrade log? Peraps it contain some useful informations

---

### Post by CelticWarrior on 2021-03-07
Please try (assuming you're still with root console):
```
apt update && apt full-upgrade
```
then try again
> do-release-upgrade

---

### Post by cereale979 on 2021-03-07
```

root@LHS3200:/etc/apt# LANG=C apt update && apt full-upgrade
Hit:1 http://old-releases.ubuntu.com/ubuntu eoan InRelease
Hit:2 http://old-releases.ubuntu.com/ubuntu eoan-security InRelease
Hit:3 http://old-releases.ubuntu.com/ubuntu eoan-updates InRelease
Hit:4 http://old-releases.ubuntu.com/ubuntu eoan-backports InRelease
Hit:5 http://old-releases.ubuntu.com/ubuntu eoan-proposed InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Calcolo dell'aggiornamento... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
root@LHS3200:/etc/apt# LANG=C do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife


Get:1 Upgrade tool signature [1554 B]                                          
Get:2 Upgrade tool [1341 kB]                                                   
Fetched 1343 kB in 0s (0 B/s)                                                  
authenticate 'focal.tar.gz' against 'focal.tar.gz.gpg' 
extracting 'focal.tar.gz'


Reading cache


Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Hit http://old-releases.ubuntu.com/ubuntu eoan InRelease                       
Hit http://old-releases.ubuntu.com/ubuntu eoan-security InRelease              
Hit http://old-releases.ubuntu.com/ubuntu eoan-updates InRelease               
Hit http://old-releases.ubuntu.com/ubuntu eoan-backports InRelease             
Hit http://old-releases.ubuntu.com/ubuntu eoan-proposed InRelease              
Fetched 0 B in 0s (0 B/s)                                                      
Reading package lists... Done    
Building dependency tree          
Reading state information... Done


Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done



```

main.log
```

2021-03-07 21:46:01,650 INFO Using config files '['./DistUpgrade.cfg']'
2021-03-07 21:46:01,650 INFO uname information: 'Linux LHS3200 5.3.0-64-generic #58-Ubuntu SMP Fri Jul 10 19:33:51 UTC 2020 x86_64'
2021-03-07 21:46:01,710 INFO apt version: '1.9.4ubuntu0.1'
2021-03-07 21:46:01,710 INFO python version: '3.7.5 (default, Apr 19 2020, 20:18:17) 
[GCC 9.2.1 20191008]'
2021-03-07 21:46:01,711 INFO release-upgrader version '20.04.29' started
2021-03-07 21:46:01,718 INFO locale: 'en_US' 'UTF-8'
2021-03-07 21:46:01,757 INFO screen could not be run
2021-03-07 21:46:01,789 DEBUG Using 'DistUpgradeViewText' view
2021-03-07 21:46:01,827 DEBUG enable dpkg --force-overwrite
2021-03-07 21:46:01,861 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2021-03-07 21:46:03,295 DEBUG lsb-release: 'eoan'
2021-03-07 21:46:03,296 DEBUG _pythonSymlinkCheck run
2021-03-07 21:46:03,297 DEBUG openCache()
2021-03-07 21:46:03,297 DEBUG quirks: running PreCacheOpen
2021-03-07 21:46:03,297 DEBUG running Quirks.PreCacheOpen
2021-03-07 21:46:03,416 DEBUG Comparing 5.3.0-62 with 
2021-03-07 21:46:03,416 DEBUG Comparing 5.3.0-64 with 5.3.0-62
2021-03-07 21:46:03,423 DEBUG /openCache(), new cache size 3277
2021-03-07 21:46:03,424 DEBUG need_server_mode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2021-03-07 21:46:03,424 DEBUG checkViewDepends()
2021-03-07 21:46:03,425 DEBUG running doUpdate() (showErrors=False)
2021-03-07 21:46:04,936 DEBUG openCache()
2021-03-07 21:46:05,066 DEBUG Comparing 5.3.0-62 with 
2021-03-07 21:46:05,066 DEBUG Comparing 5.3.0-64 with 5.3.0-62
2021-03-07 21:46:05,074 DEBUG /openCache(), new cache size 3277
2021-03-07 21:46:05,074 DEBUG doPostInitialUpdate
2021-03-07 21:46:05,074 DEBUG quirks: running focalPostInitialUpdate
2021-03-07 21:46:05,074 DEBUG running Quirks.focalPostInitialUpdate
2021-03-07 21:46:55,114 DEBUG abort called
2021-03-07 21:46:55,115 DEBUG openCache()
2021-03-07 21:46:55,246 DEBUG Comparing 5.3.0-62 with 
2021-03-07 21:46:55,246 DEBUG Comparing 5.3.0-64 with 5.3.0-62
2021-03-07 21:46:55,253 DEBUG /openCache(), new cache size 3277


```

---

### Post by cereale979 on 2021-03-07
Probably I've found the solution here:

```
https://askubuntu.com/questions/1281969/ubuntu-20-04-1-upgrade-failure-error-dist-upgrade-failed-broken-packages-aft
```

I've commit this instruction "apt-get remove colord" and after the removal i've commit "do-release-upgrade" and now we've passed to the next step.... crossed fingers

---

