---
title: "Upgrade tool crashed near the end of installing packages - How do I rerun it?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by andyanderso on 2008-04-26
Very near the end of installing my new packages the upgrade tool for Hardy crashed.  It did not do the clean step or the restarting step.  I ran autoremove and autoclean and restarted.  Everything seems to work fine.  Apt-get finds no updates but there are still several packages in the local (installed or obselete) filter in synaptic.  Php, apache and MySQL seemed to be causing the upgrade some problems but hey all seem to work fine now. How can I rerun the Hardy upgrade to make sure everything installed and all is well?

andy

---

### Post by James- on 2008-04-26
try this:
```
sudo apt-get -f install
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by andyanderso on 2008-04-26
> **James- said:**
> try this:
```
sudo apt-get -f install
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```
I did that and it seems to think everything is just fine.  Here is the output:
[INDENT]andy@hermes:~$ sudo apt-get -f install
[sudo] password for andy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andy@hermes:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 [http://planet76.com](http://planet76.com) ./ Release.gpg [189B]
Ign [http://planet76.com](http://planet76.com) ./ Translation-en_CA                                   
Get:2 [http://planet76.com](http://planet76.com) ./ Release [438B]                                    
Ign [http://planet76.com](http://planet76.com) ./ Release                                             
Ign [http://planet76.com](http://planet76.com) ./ Packages                                            
Hit [http://planet76.com](http://planet76.com) ./ Packages                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_CA
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_CA
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_CA
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_CA
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_CA
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_CA
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_CA
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_CA
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Fetched 190B in 4s (39B/s)
Reading package lists... Done
W: GPG error: [http://planet76.com](http://planet76.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2F355BA8FB4A41C3
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andy@hermes:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andy@hermes:~$ 
[/INDENT]
so I guess it crashed after it was done?

---

### Post by James- on 2008-04-27
if you have the gnome interface go into the about screen and it should say 8.04

---

