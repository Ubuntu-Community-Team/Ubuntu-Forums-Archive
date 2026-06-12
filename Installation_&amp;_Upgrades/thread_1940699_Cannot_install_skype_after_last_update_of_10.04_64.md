---
title: "Cannot install skype after last update of 10.04 64bit"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by centralniak on 2012-03-14
Hi guys,

After yesterday's update of Ubuntu 10.04LTS Desktop 64bit I cannot install skype. What I try is:

```
aptitude install skype
```The output is:

```
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Odczyt dodatkowych informacji o stanie      
Inicjalizacja stanów pakietów... Gotowe
Nast&#281;puj&#261;ce pakiety maj&#261; NIESPE&#321;NIONE zale&#380;no&#347;ci:
  lib32asound2 libc6-i386 
Nast&#281;puj&#261;ce NOWE pakiety zostan&#261; zainstalowane:
  ia32-libs{a} lib32bz2-1.0{a} lib32gcc1{a} lib32ncurses5{a} 
  lib32stdc++6{a} lib32v4l-0{a} lib32z1{a} skype 
0 pakietów aktualizowanych, 10 instalowanych, 0 do usuni&#281;cia i 1 nie aktualizowanych.
Do pobrania 61,0MB/64,9MB archiwów. Zaj&#281;te po rozpakowaniu: 202MB.
Nast&#281;puj&#261;ce pakiety maj&#261; niespe&#322;nione zale&#380;no&#347;ci:
  libc6-i386: Wymaga: libc6 (= 2.13-0ubuntu13) ale zainstalowana jest wersja 2.11.1-0ubuntu7.10.
  lib32asound2: Wymaga: libasound2 (= 1.0.24.1-0ubuntu5) ale zainstalowana jest wersja 1.0.22-0ubuntu7.
Nast&#281;puj&#261;ce dzia&#322;ania rozwi&#261;&#380;&#261; problemy z zale&#380;no&#347;ciami:

Instalacja nast&#281;puj&#261;cych pakietów:
lib32asound2 [1.0.22-0ubuntu7 (lucid, now)]
libc6-i386 [2.11.1-0ubuntu7.10 (lucid-security, lucid-updates)]

Wynik: -10

Zaakceptowa&#263; rozwi&#261;zanie? [T/n/q/?]
```As you can maybe guess, there are some broken dependencies. I've tried installing the libraries by hand, which didn't help. I've changed the repository server from Polish to main. Also tried to accept the aptitude solution (pressed T or t) but it gave me 'wrong answer' message. 

I've also tried, as root:

```
dpkg -a
aptitude update && aptitude upgrade
apt-get -f install
```But to no success...

Also did steps at:
[https://help.ubuntu.com/community/SynapticHowto#How_to_fix_broken_packages](https://help.ubuntu.com/community/SynapticHowto#How_to_fix_broken_packages)

Do you have any suggestions what to do? Any help appreciated!

P.S. I could not complete the update yesterday until I uninstalled Skype. I hoped I could reinstall it simply later, but no...

---

### Post by raja.genupula on 2012-03-14
please post the code of what you got in terminal . 
your language a bit problem to me . 
what it gave you when you had typed ```
sudo apt-get install -f
```

---

### Post by centralniak on 2012-03-14
Hehe, yepp, the language :)

```
piotr@piotr-dell:~$ sudo apt-get install -f
[sudo] password for piotr: 
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 1 nieaktualizowanych.

```0 updated, 0 installed, 0 deleted and 1 not updated
Gotowe means ready (success)

---

### Post by raja.genupula on 2012-03-14
ok try this and will you please switch your language to english  up to solving this issue . 

```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
```


```
sudo apt-get update && sudo apt-get install skype
```

do them line by line in your terminal and let us know what you got . 

all the best

---

### Post by centralniak on 2012-03-14
piotr@piotr-dell:~$ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"

```

[sudo] password for piotr: 
```piotr@piotr-dell:~$ sudo apt-get update && sudo apt-get install skype
```
Hit http://packages.medibuntu.org lucid Release.gpg
Hit http://archive.canonical.com lucid Release.gpg                                                                                                                             
Hit http://archive.ubuntu.com lucid Release.gpg                                                                                                                                                     
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB                                                                                                                            
Get: 1 http://archive.canonical.com lucid Release.gpg [198B]                                                                                                                                        
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/ natty/main Translation-en_GB                                                                                                 
Get: 2 http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB [62.9kB]                                                                                                                      
Ign http://archive.canonical.com/ lucid/partner Translation-en_GB                                                                                                                                   
Ign http://packages.medibuntu.org/ lucid/free Translation-en_GB                                                                                                                                     
Hit http://deb.opera.com stable Release.gpg                                                                                                                                                         
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_GB                                                                                                                                   
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/ natty/restricted Translation-en_GB                                                                                           
Get: 3 http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB [2,332B]                                                                                                                
Get: 4 http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB [33.9kB]                                                                                                                  
Get: 5 http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB [37.7kB]                                                                                                                
Hit http://archive.canonical.com lucid Release                                                                                                                                                      
Get: 6 http://archive.canonical.com lucid Release [8,215B]                                                                                                                                          
Hit http://linux.dropbox.com lucid Release.gpg                                                                                                                                                      
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_GB                                                                                                                                   
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_GB                                                                                                                                 
Hit http://packages.medibuntu.org lucid Release                                                                                                                                                     
Hit http://deb.opera.com stable Release                                                                                                                                                             
Hit http://archive.ubuntu.com lucid-security Release.gpg                                                                                                                                            
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB                                                        
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB                                                  
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB                                                    
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB                                                  
Hit http://archive.ubuntu.com lucid-updates Release.gpg                                                                            
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB                                                   
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB                                                         
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB                                                   
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB                                                                  
Hit http://archive.ubuntu.com lucid Release                                                                      
Hit http://linux.dropbox.com lucid Release                                                                         
Hit http://archive.ubuntu.com lucid-security Release                                                               
Hit http://archive.ubuntu.com lucid-updates Release                                                              
Get: 7 http://dl.google.com stable Release.gpg [198B]                                                            
Hit http://archive.canonical.com lucid/partner Packages                                                                                                
Get: 8 http://archive.canonical.com lucid/partner Packages [12.9kB]                                                                                    
Hit http://packages.medibuntu.org lucid/free Packages                                                                                                  
Ign http://deb.opera.com stable/non-free Packages                                                                                                    
Ign http://deb.opera.com stable/non-free Packages                                                                                                                                                   
Hit http://packages.medibuntu.org lucid/non-free Packages                                                                                                         
Hit http://archive.ubuntu.com lucid/main Packages                                                                                           
Hit http://deb.opera.com stable/non-free Packages                                                                     
Hit http://archive.ubuntu.com lucid/restricted Packages                                         
Hit http://archive.ubuntu.com lucid/main Sources                                                
Hit http://archive.ubuntu.com lucid/restricted Sources                    
Hit http://archive.ubuntu.com lucid/universe Packages                     
Hit http://archive.ubuntu.com lucid/universe Sources                      
Hit http://linux.dropbox.com lucid/main Packages                          
Ign http://mirror.sifnt.net.au jaunty Release.gpg                         
Hit http://archive.ubuntu.com lucid/multiverse Packages                   
Hit http://archive.ubuntu.com lucid/multiverse Sources                             
Hit http://archive.ubuntu.com lucid-security/main Packages                         
Hit http://archive.ubuntu.com lucid-security/restricted Packages                   
Hit http://archive.ubuntu.com lucid-security/main Sources                          
Hit http://archive.ubuntu.com lucid-security/restricted Sources                    
Hit http://archive.ubuntu.com lucid-security/universe Packages                     
Hit http://archive.ubuntu.com lucid-security/universe Sources                      
Hit http://archive.ubuntu.com lucid-security/multiverse Packages                                         
Hit http://archive.ubuntu.com lucid-security/multiverse Sources                                          
Hit http://archive.ubuntu.com lucid-updates/restricted Packages                                          
Hit http://archive.ubuntu.com lucid-updates/main Packages                                                
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages                                          
Hit http://archive.ubuntu.com lucid-updates/universe Packages                                            
Ign http://mirror.sifnt.net.au/linux/ jaunty/main Translation-en_GB                                      
Ign http://mirror.sifnt.net.au jaunty Release       
Ign http://mirror.sifnt.net.au jaunty/main Packages
Ign http://mirror.sifnt.net.au jaunty/main Sources
Ign http://mirror.sifnt.net.au jaunty/main Packages
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_GB
Ign http://mirror.sifnt.net.au jaunty/main Sources
Hit http://mirror.sifnt.net.au jaunty/main Packages
Hit http://mirror.sifnt.net.au jaunty/main Sources
Get: 9 http://dl.google.com stable Release [1,351B]                                                                                                                                                 
Get: 10 http://dl.google.com stable/main Packages [1,267B]                                                                                                                                          
Fetched 161kB in 11s (13.7kB/s)                                                                                                                                                                     
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  skype: Depends: ia32-libs (>= 2.4) but it is not going to be installed
         Depends: lib32asound2 (> 1.0.22) but it is not going to be installed
         Depends: lib32gcc1 (>= 1:4.1.1) but it is not going to be installed
         Depends: lib32stdc++6 (>= 4.2.1) but it is not going to be installed
         Depends: libc6-i386 (>= 2.4) but it is not going to be installed
E: Broken packages

```

---

### Post by mikewhatever on 2012-03-14
You seem to have some sources for Jaunty (9.04). Try removing them, as the distro you use is Lucid.

---

### Post by raja.genupula on 2012-03-14
now try doing 
```
sudo apt-get install -f
```

---

### Post by centralniak on 2012-03-14
> **mikewhatever said:**
> You seem to have some sources for Jaunty (9.04). Try removing them, as the distro you use is Lucid.

Yes I did that, and then:
```
sudo apt-get update && sudo apt-get install skype
```To this effect:
```
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/ natty/main Translation-en_GB
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/ natty/restricted Translation-en_GB                                                                                           
Hit http://packages.medibuntu.org lucid Release.gpg                                                                                                                                                 
Hit http://deb.opera.com stable Release.gpg                                                                                                                                                         
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_GB                                                                                                                                   
Hit http://archive.canonical.com lucid Release.gpg                                                                                                                                                  
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB                                                                                                                           
Hit http://archive.ubuntu.com lucid Release.gpg                                                                                        
Hit http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB                                                                                           
Hit http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB                                                                                     
Ign http://packages.medibuntu.org/ lucid/free Translation-en_GB                                                                                              
Hit http://archive.canonical.com lucid Release.gpg                                                                                     
Ign http://archive.canonical.com/ lucid/partner Translation-en_GB                                                                                 
Hit http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB                                                                                                  
Hit http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB                                                                                                
Hit http://archive.ubuntu.com lucid-security Release.gpg                                                                                          
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB                                                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB                                                                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB                                                                                         
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB                                                                                       
Hit http://archive.ubuntu.com lucid-updates Release.gpg                                                                                                                 
Hit http://archive.canonical.com lucid Release                                                                                                                          
Hit http://deb.opera.com stable Release                                                                                                                                                       
Hit http://archive.canonical.com lucid Release                                                                                                                          
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB                                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB                                                                               
Hit http://archive.ubuntu.com lucid Release                                                                                                                  
Hit http://archive.ubuntu.com lucid-security Release                                                                                                         
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_GB                                                                                          
Hit http://archive.canonical.com lucid/partner Packages                                                                                                                                       
Hit http://archive.ubuntu.com lucid-updates Release                                                                                                                     
Hit http://linux.dropbox.com lucid Release.gpg                                                                                                                          
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_GB                                                                                                                             
Ign http://deb.opera.com stable/non-free Packages                                                                                                                                             
Hit http://archive.canonical.com lucid/partner Packages                                                                                           
Hit http://archive.ubuntu.com lucid/main Packages                                          
Hit http://archive.ubuntu.com lucid/restricted Packages                                    
Hit http://archive.ubuntu.com lucid/main Sources                                           
Hit http://archive.ubuntu.com lucid/restricted Sources                                     
Hit http://archive.ubuntu.com lucid/universe Packages                                      
Hit http://packages.medibuntu.org lucid Release                                            
Hit http://archive.ubuntu.com lucid/universe Sources                                       
Hit http://archive.ubuntu.com lucid/multiverse Packages                                    
Hit http://archive.ubuntu.com lucid/multiverse Sources               
Hit http://archive.ubuntu.com lucid-security/main Packages           
Hit http://archive.ubuntu.com lucid-security/restricted Packages     
Ign http://deb.opera.com stable/non-free Packages                    
Hit http://archive.ubuntu.com lucid-security/main Sources                                             
Hit http://archive.ubuntu.com lucid-security/restricted Sources                                       
Hit http://archive.ubuntu.com lucid-security/universe Packages                                        
Hit http://archive.ubuntu.com lucid-security/universe Sources                                                               
Hit http://archive.ubuntu.com lucid-security/multiverse Packages                                                            
Hit http://archive.ubuntu.com lucid-security/multiverse Sources                                                             
Hit http://archive.ubuntu.com lucid-updates/restricted Packages                                                             
Hit http://archive.ubuntu.com lucid-updates/main Packages                                                                   
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages                                                  
Hit http://archive.ubuntu.com lucid-updates/universe Packages                                                    
Hit http://linux.dropbox.com lucid Release                                                                       
Hit http://deb.opera.com stable/non-free Packages                                                                
Hit http://packages.medibuntu.org lucid/free Packages                                      
Hit http://packages.medibuntu.org lucid/non-free Packages                       
Hit http://linux.dropbox.com lucid/main Packages                                
Get: 1 http://dl.google.com stable Release.gpg [198B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_GB
Get: 2 http://dl.google.com stable Release [1,351B]
Get: 3 http://dl.google.com stable/main Packages [1,267B]                                                                                                                                           
Fetched 2,816B in 8s (343B/s)                                                                                                                                                                       
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  skype: Depends: ia32-libs (>= 2.4) but it is not going to be installed
         Depends: lib32asound2 (> 1.0.22) but it is not going to be installed
         Depends: lib32gcc1 (>= 1:4.1.1) but it is not going to be installed
         Depends: lib32stdc++6 (>= 4.2.1) but it is not going to be installed
         Depends: libc6-i386 (>= 2.4) but it is not going to be installed
E: Broken packages
```

I don't think that the duplicates cause the bugs, I can remove them though...

---

### Post by centralniak on 2012-03-14
Thanks for your time so far! 

> **raja.genupula said:**
> now try doing 
```
sudo apt-get install -f
```

```
piotr@piotr-dell:/etc$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by raja.genupula on 2012-03-15
open your synaptic and look for those required pkgs in search box and install them from there with required version .

---

### Post by centralniak on 2012-03-15
> **raja.genupula said:**
> open your synaptic and look for those required pkgs in search box and install them from there with required version .

Sorry, I don't have libc6-i386 (>= 2.4) available for install  - the latest version in Synaptic is 2.13-0ubuntu13

---

### Post by raja.genupula on 2012-03-15
[http://packages.ubuntu.com/search?searchon=names&keywords=libc6](http://packages.ubuntu.com/search?searchon=names&keywords=libc6)

---

### Post by centralniak on 2012-03-16
Yes it worked, thank you so much!

Shall I cleanup sources.list now somehow?

---

### Post by mikewhatever on 2012-03-17
Hm..., so what worked exactly? The highest libc in that list is 2.15, not >=2.4.

---

