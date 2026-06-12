---
title: "Pb updating initramfs-tools"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by Pierre771 on 2013-10-27
Hello

I've had pb with initramfs for a few weeks

I am using Netrunner 13.06, a distribution derivated from Ubuntu 13.04

Cf below. Can you help me please

```
pierre@pierre-K73SV:~$ sudo apt-get -f install
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
1 partiellement installés ou enlevés.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Paramétrage de initramfs-tools (0.103ubuntu0.8) ...
update-initramfs: deferring update (trigger activated)
Traitement des actions différées («*triggers*») pour «*initramfs-tools*»...
update-initramfs: Generating /boot/initrd.img-3.8.0-23-generic
cp: impossible d'évaluer «/module-files.d/libpango1.0-0.modules»: Aucun fichier ou dossier de ce type
cp: impossible d'évaluer «/modules/pango-basic-fc.so»: Aucun fichier ou dossier de ce type
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-23-generic with 1.
dpkg: erreur de traitement de initramfs-tools (--configure)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 1
Des erreurs ont été rencontrées pendant l'exécution*:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
pierre@pierre-K73SV:~$ 

```

---

### Post by Pierre771 on 2013-10-27
Fixed (found in the current forum)

```
pierre@pierre-K73SV:~$ sudo rm -f /var/lib/dpkg/info/initramfs-tools.post*
[sudo] password for pierre: 
pierre@pierre-K73SV:~$ sudo rm -f /var/lib/dpkg/info/initramfs-tools.pre*
pierre@pierre-K73SV:~$ sudo rm -f /var/lib/dpkg/info/bcmwl-kernel-source.post*
pierre@pierre-K73SV:~$ sudo rm -f /var/lib/dpkg/info/bcmwl-kernel-source.pre*
pierre@pierre-K73SV:~$ sudo dpkg --configure -a
Paramétrage de initramfs-tools (0.103ubuntu0.8) ...
pierre@pierre-K73SV:~$ sudo apt-get update
Atteint http://dl.google.com stable Release.gpg
Atteint http://ppa.launchpad.net raring Release.gpg                            
Atteint http://dl.google.com stable Release.gpg                                
Atteint http://ppa.launchpad.net raring Release.gpg                            
Atteint http://dl.google.com stable Release                                    
Atteint http://ppa.launchpad.net raring Release.gpg                            
Atteint http://security.ubuntu.com raring-security Release.gpg                 
Atteint http://dl.google.com stable Release                                    
Atteint http://packages.netrunner-os.com enigma-1306 Release.gpg               
Atteint http://ppa.launchpad.net raring Release.gpg                            
Atteint http://security.ubuntu.com raring-security Release                     
Atteint http://dl.google.com stable/main amd64 Packages                        
Atteint http://archive.ubuntu.com raring Release.gpg                           
Atteint http://ppa.launchpad.net raring Release.gpg                            
Atteint http://packages.netrunner-os.com enigma-1306 Release                   
Atteint http://dl.google.com stable/main i386 Packages                         
Atteint http://ppa.launchpad.net raring Release                                
Réception de*: 1 http://archive.ubuntu.com raring-updates Release.gpg [933 B]  
Atteint http://security.ubuntu.com raring-security/main amd64 Packages         
Atteint http://archive.canonical.com raring Release.gpg                        
Atteint http://packages.netrunner-os.com enigma-1306/main amd64 Packages       
Atteint http://ppa.launchpad.net raring Release                                
Atteint http://archive.ubuntu.com raring Release                               
Atteint http://security.ubuntu.com raring-security/restricted amd64 Packages   
Atteint http://archive.canonical.com raring Release                            
Atteint http://packages.netrunner-os.com enigma-1306/main i386 Packages        
Atteint http://ppa.launchpad.net raring Release                                
Atteint http://security.ubuntu.com raring-security/universe amd64 Packages     
Réception de*: 2 http://archive.ubuntu.com raring-updates Release [40,8 kB]    
Atteint http://archive.canonical.com raring/partner amd64 Packages             
Atteint http://ppa.launchpad.net raring Release                                
Atteint http://security.ubuntu.com raring-security/multiverse amd64 Packages   
Atteint http://archive.canonical.com raring/partner i386 Packages              
Atteint http://ppa.launchpad.net raring Release                                
Atteint http://dl.google.com stable/main amd64 Packages                        
Atteint http://security.ubuntu.com raring-security/main i386 Packages          
Atteint http://ppa.launchpad.net raring/main amd64 Packages                    
Atteint http://dl.google.com stable/main i386 Packages                         
Atteint http://archive.ubuntu.com raring/main amd64 Packages                   
Atteint http://security.ubuntu.com raring-security/restricted i386 Packages    
Atteint http://ppa.launchpad.net raring/main i386 Packages                     
Atteint http://archive.ubuntu.com raring/restricted amd64 Packages             
Atteint http://security.ubuntu.com raring-security/universe i386 Packages      
Atteint http://archive.ubuntu.com raring/universe amd64 Packages               
Atteint http://security.ubuntu.com raring-security/multiverse i386 Packages    
Atteint http://archive.ubuntu.com raring/multiverse amd64 Packages             
Atteint http://archive.ubuntu.com raring/main i386 Packages                    
Atteint http://ppa.launchpad.net raring/main amd64 Packages                    
Atteint http://archive.ubuntu.com raring/restricted i386 Packages              
Atteint http://security.ubuntu.com raring-security/main Translation-en         
Atteint http://archive.ubuntu.com raring/universe i386 Packages                
Atteint http://archive.ubuntu.com raring/multiverse i386 Packages              
Atteint http://ppa.launchpad.net raring/main i386 Packages                     
Atteint http://security.ubuntu.com raring-security/multiverse Translation-en   
Atteint http://archive.ubuntu.com raring/main Translation-fr                   
Atteint http://archive.ubuntu.com raring/main Translation-en                   
Ign http://packages.netrunner-os.com enigma-1306/main Translation-fr_FR        
Atteint http://ppa.launchpad.net raring/main amd64 Packages                    
Ign http://archive.canonical.com raring/partner Translation-fr_FR              
Atteint http://archive.ubuntu.com raring/multiverse Translation-fr             
Ign http://packages.netrunner-os.com enigma-1306/main Translation-fr           
Atteint http://ppa.launchpad.net raring/main i386 Packages                     
Ign http://archive.canonical.com raring/partner Translation-fr                 
Atteint http://security.ubuntu.com raring-security/restricted Translation-en   
Ign http://packages.netrunner-os.com enigma-1306/main Translation-en           
Ign http://archive.canonical.com raring/partner Translation-en                 
Atteint http://archive.ubuntu.com raring/multiverse Translation-en             
Atteint http://security.ubuntu.com raring-security/universe Translation-en     
Atteint http://archive.ubuntu.com raring/restricted Translation-fr             
Atteint http://ppa.launchpad.net raring/main amd64 Packages                    
Atteint http://archive.ubuntu.com raring/restricted Translation-en             
Atteint http://ppa.launchpad.net raring/main i386 Packages                     
Atteint http://archive.ubuntu.com raring/universe Translation-fr               
Atteint http://archive.ubuntu.com raring/universe Translation-en               
Réception de*: 3 http://archive.ubuntu.com raring-updates/main amd64 Packages [201 kB]
Atteint http://ppa.launchpad.net raring/main amd64 Packages                    
Atteint http://ppa.launchpad.net raring/main i386 Packages                     
Ign http://dl.google.com stable/main Translation-fr_FR                         
Ign http://dl.google.com stable/main Translation-fr                            
Ign http://dl.google.com stable/main Translation-en                            
Réception de*: 4 http://archive.ubuntu.com raring-updates/restricted amd64 Packages [14 B]
Ign http://dl.google.com stable/main Translation-fr_FR                         
Réception de*: 5 http://archive.ubuntu.com raring-updates/universe amd64 Packages [153 kB]
Ign http://dl.google.com stable/main Translation-fr                            
Ign http://dl.google.com stable/main Translation-en                            
Réception de*: 6 http://archive.ubuntu.com raring-updates/multiverse amd64 Packages [3 715 B]
Réception de*: 7 http://archive.ubuntu.com raring-updates/main i386 Packages [199 kB]
Réception de*: 8 http://archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]
Réception de*: 9 http://archive.ubuntu.com raring-updates/universe i386 Packages [154 kB]
Réception de*: 10 http://archive.ubuntu.com raring-updates/multiverse i386 Packages [3 864 B]
Atteint http://archive.ubuntu.com raring-updates/main Translation-en           
Ign http://security.ubuntu.com raring-security/main Translation-fr_FR          
Atteint http://archive.ubuntu.com raring-updates/multiverse Translation-en
Ign http://security.ubuntu.com raring-security/main Translation-fr      
Ign http://security.ubuntu.com raring-security/multiverse Translation-fr_FR
Ign http://security.ubuntu.com raring-security/multiverse Translation-fr
Atteint http://archive.ubuntu.com raring-updates/restricted Translation-en
Ign http://security.ubuntu.com raring-security/restricted Translation-fr_FR
Ign http://security.ubuntu.com raring-security/restricted Translation-fr
Atteint http://archive.ubuntu.com raring-updates/universe Translation-en
Ign http://security.ubuntu.com raring-security/universe Translation-fr_FR
Ign http://security.ubuntu.com raring-security/universe Translation-fr  
Ign http://ppa.launchpad.net raring/main Translation-fr_FR              
Ign http://ppa.launchpad.net raring/main Translation-fr                 
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-fr_FR
Ign http://ppa.launchpad.net raring/main Translation-fr
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-fr_FR
Ign http://ppa.launchpad.net raring/main Translation-fr
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-fr_FR
Ign http://ppa.launchpad.net raring/main Translation-fr
Ign http://archive.ubuntu.com raring/main Translation-fr_FR
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://archive.ubuntu.com raring/multiverse Translation-fr_FR
Ign http://ppa.launchpad.net raring/main Translation-fr_FR
Ign http://archive.ubuntu.com raring/restricted Translation-fr_FR
Ign http://ppa.launchpad.net raring/main Translation-fr
Ign http://archive.ubuntu.com raring/universe Translation-fr_FR
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://archive.ubuntu.com raring-updates/main Translation-fr_FR
Ign http://archive.ubuntu.com raring-updates/main Translation-fr
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-fr_FR
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-fr
Ign http://archive.ubuntu.com raring-updates/restricted Translation-fr_FR
Ign http://archive.ubuntu.com raring-updates/restricted Translation-fr
Ign http://archive.ubuntu.com raring-updates/universe Translation-fr_FR
Ign http://archive.ubuntu.com raring-updates/universe Translation-fr
757 ko réceptionnés en 4s (152 ko/s)
Lecture des listes de paquets... Fait
pierre@pierre-K73SV:~$ sudo apt-get dist-upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Calcul de la mise à jour... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
pierre@pierre-K73SV:~$ sudo apt-get -f install
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
pierre@pierre-K73SV:~$ 

```

---

