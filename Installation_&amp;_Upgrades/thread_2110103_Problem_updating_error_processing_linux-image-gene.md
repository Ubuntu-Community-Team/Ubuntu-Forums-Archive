---
title: "Problem updating: error processing linux-image-generic"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by fleneh on 2013-01-29
Hello.
I have Ubuntu 12.04. When I try to get updates via apt-get update and apt-get upgrade i recive this error: (sorry, my ubuntu is in catalan language)

S'està configurant linux-image-3.2.0-35-generic (3.2.0-35.55)…
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: If: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic.postinst line 1010.
dpkg: s'ha produït un error en processar linux-image-3.2.0-35-generic (--configure):
 el subprocés s'ha insta&#320;lat el script post-installation retornà el codi d'eixida d'error 2
S'està configurant linux-image-3.2.0-36-generic (3.2.0-36.57)…
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: If: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-36-generic.postinst line 1010.
dpkg: s'ha produït un error en processar linux-image-3.2.0-36-generic (--configure):
 el subprocés s'ha insta&#320;lat el script post-installation retornà el codi d'eixida d'error 2
dpkg: problemes de dependències impedeixen la configuració de linux-image-generic:
 linux-image-generic depèn de linux-image-3.2.0-35-generic; tot i així:
  El paquet linux-image-3.2.0-35-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-image-generic (--configure):
 problemes de dependències - es deixa sense configurar
dpkg: problemes de dependències impedeixen la configuració de linux-generic:
 linux-generic depèn de linux-image-generic (= 3.2.0.35.40); tot i així:
  El paquet linux-image-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-generic (--configure):
 problemes de dependències - es deixa sense configurar
No s'ha escrit cap informe perquè el missatge d'error indica que és un error consequent de una fallida anterior.
                        No s'ha escrit cap informe perquè ja s'ha superat MaxReports
                                                                                    S'han trobat errors en processar:
 linux-image-3.2.0-35-generic
 linux-image-3.2.0-36-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Cheesehead on 2013-01-29
The current version in the repos is 3.2.0.36.43 (or .44 in -proposed), not 3.2.0-35.55

Check that you are using a good mirror.
Then do  [FONT="Courier New"]sudo apt-get update[/FONT] again to refresh your sources and change the target to the current version.
Then try upgrading again.

---

### Post by fleneh on 2013-01-29
First of all I should say that I am a noob using Ubuntu, I have been using it for 2 months.
I can't update it via apt-get update, neither from synaptic. I have tried to download the package "linux-image-generic" 3.2.0.36.43 from [http://www.ubuntuupdates.org/package/core/precise/main/security/linux-image-generic](http://www.ubuntuupdates.org/package/core/precise/main/security/linux-image-generic) but I can't install it. 
btw when I try to update via synaptic I get the same error:
Error processing: 
 linux-image-3.2.0-35-generic
 linux-image-3.2.0-36-generic
 linux-image-generic
 linux-generic

---

### Post by Old_Grey_Wolf on 2013-01-29
The forum members need to find out what is wrong with your sources.list file or possibly something else. You shouldn't need to download the current Linux kernel package for 12.04 and install it manually.

What is the output of entering ```
sudo apt-get update
```in the terminal? Please post the output between the # {code} button tags.

What is the output of entering ```
sudo apt-get upgrade
```in the terminal? Please post the output between the # {code} button tags.

Your problem is also requiring a Kernel upgrade; therefore, what is the output of entering ```
sudo apt-get dist-upgrade
```in the terminal? Please post the output between the # {code} button tags.

If you do not fix the root cause of the problem, it will keep happening again and again.

---

### Post by fleneh on 2013-01-30
When I enter sudo apt-get update:

```
Obj http://packages.medibuntu.org precise InRelease
Ign http://es.archive.ubuntu.com precise InRelease                             
Ign http://archive.canonical.com precise InRelease                             
Obj http://repository.spotify.com stable InRelease                             
Obj http://deb.playonlinux.com precise InRelease                               
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Obj http://archive.canonical.com precise Release.gpg                           
Obj http://repository.spotify.com stable/non-free amd64 Packages               
Obj http://deb.playonlinux.com precise/main amd64 Packages                     
Obj http://ppa.launchpad.net precise Release.gpg                               
Obj http://ppa.launchpad.net precise Release.gpg                               
Obj http://ppa.launchpad.net precise Release.gpg                               
Obj http://ppa.launchpad.net precise Release.gpg                               
Obj http://ppa.launchpad.net precise Release.gpg                               
Bai:1 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Obj http://packages.medibuntu.org precise/free Sources                         
Obj http://archive.canonical.com precise Release                               
Obj http://repository.spotify.com stable/non-free i386 Packages                
Ign http://repository.spotify.com stable/non-free TranslationIndex             
Obj http://deb.playonlinux.com precise/main i386 Packages                      
Obj http://ppa.launchpad.net precise Release.gpg                               
Obj http://ppa.launchpad.net precise Release                                   
Obj http://ppa.launchpad.net precise Release                                   
Obj http://ppa.launchpad.net precise Release                                   
Obj http://ppa.launchpad.net precise Release                                   
Obj http://extras.ubuntu.com precise Release                                   
Bai:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Obj http://packages.medibuntu.org precise/non-free Sources                     
Obj http://archive.canonical.com precise/partner Sources                       
Ign http://deb.playonlinux.com precise/main TranslationIndex                   
Obj http://archive.canonical.com precise/partner amd64 Packages                
Obj http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Obj http://packages.medibuntu.org precise/free amd64 Packages                  
Obj http://extras.ubuntu.com precise/main Sources                              
Bai:3 http://security.ubuntu.com precise-security Release [49,6 kB]            
Obj http://ppa.launchpad.net precise Release                                   
Obj http://ppa.launchpad.net precise Release                                   
Obj http://packages.medibuntu.org precise/non-free amd64 Packages              
Obj http://extras.ubuntu.com precise/main amd64 Packages                       
Obj http://extras.ubuntu.com precise/main i386 Packages                        
Obj http://ppa.launchpad.net precise/main Sources                              
Obj http://ppa.launchpad.net precise/main amd64 Packages                       
Obj http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Obj http://ppa.launchpad.net precise/main Sources                              
Obj http://ppa.launchpad.net precise/main amd64 Packages                       
Obj http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Obj http://packages.medibuntu.org precise/free i386 Packages                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Obj http://ppa.launchpad.net precise/main Sources                              
Obj http://ppa.launchpad.net precise/main amd64 Packages                       
Obj http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Obj http://ppa.launchpad.net precise/main Sources                              
Obj http://ppa.launchpad.net precise/main amd64 Packages                       
Obj http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Obj http://ppa.launchpad.net precise/main Sources                              
Obj http://packages.medibuntu.org precise/non-free i386 Packages               
Obj http://ppa.launchpad.net precise/main amd64 Packages                       
Obj http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Obj http://ppa.launchpad.net precise/main Sources                              
Obj http://ppa.launchpad.net precise/main amd64 Packages                       
Obj http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://repository.spotify.com stable/non-free Translation-ca_ES            
Ign http://archive.canonical.com precise/partner Translation-ca_ES             
Ign http://repository.spotify.com stable/non-free Translation-ca               
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Ign http://archive.canonical.com precise/partner Translation-ca                
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://repository.spotify.com stable/non-free Translation-en               
Bai:4 http://security.ubuntu.com precise-security/main Sources [61,9 kB]       
Ign http://deb.playonlinux.com precise/main Translation-ca_ES                  
Ign http://deb.playonlinux.com precise/main Translation-ca                     
Ign http://extras.ubuntu.com precise/main Translation-ca_ES                    
Ign http://deb.playonlinux.com precise/main Translation-en                     
Ign http://extras.ubuntu.com precise/main Translation-ca                       
Ign http://extras.ubuntu.com precise/main Translation-en                       
Bai:5 http://security.ubuntu.com precise-security/restricted Sources [1950 B]  
Bai:6 http://security.ubuntu.com precise-security/universe Sources [20,0 kB]   
Bai:7 http://security.ubuntu.com precise-security/multiverse Sources [1379 B]  
Bai:8 http://security.ubuntu.com precise-security/main amd64 Packages [221 kB] 
Ign http://ppa.launchpad.net precise/main Translation-ca_ES                    
Ign http://ppa.launchpad.net precise/main Translation-ca                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-ca_ES                    
Ign http://ppa.launchpad.net precise/main Translation-ca                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-ca_ES                    
Ign http://ppa.launchpad.net precise/main Translation-ca                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-ca_ES                    
Ign http://ppa.launchpad.net precise/main Translation-ca                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-ca_ES                    
Ign http://ppa.launchpad.net precise/main Translation-ca                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-ca_ES                    
Ign http://ppa.launchpad.net precise/main Translation-ca                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Bai:9 http://security.ubuntu.com precise-security/restricted amd64 Packages [3969 B]
Bai:10 http://security.ubuntu.com precise-security/universe amd64 Packages [61,9 kB]
Bai:11 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2184 B]
Bai:12 http://security.ubuntu.com precise-security/main i386 Packages [229 kB] 
Ign http://es.archive.ubuntu.com precise-updates InRelease                     
Ign http://es.archive.ubuntu.com precise-backports InRelease                   
Bai:13 http://security.ubuntu.com precise-security/restricted i386 Packages [3968 B]
Bai:14 http://security.ubuntu.com precise-security/universe i386 Packages [63,2 kB]
Bai:15 http://security.ubuntu.com precise-security/multiverse i386 Packages [2366 B]
Bai:16 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Bai:17 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Bai:18 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Bai:19 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Obj http://security.ubuntu.com precise-security/main Translation-en            
Obj http://security.ubuntu.com precise-security/multiverse Translation-en      
Obj http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://packages.medibuntu.org precise/free Translation-ca_ES               
Obj http://security.ubuntu.com precise-security/universe Translation-en   
Ign http://packages.medibuntu.org precise/free Translation-ca                  
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-ca_ES           
Ign http://packages.medibuntu.org precise/non-free Translation-ca              
Ign http://packages.medibuntu.org precise/non-free Translation-en
Obj http://es.archive.ubuntu.com precise Release.gpg
Bai:20 http://es.archive.ubuntu.com precise-updates Release.gpg [198 B]
Obj http://es.archive.ubuntu.com precise-backports Release.gpg
Obj http://es.archive.ubuntu.com precise Release                               
Bai:21 http://es.archive.ubuntu.com precise-updates Release [49,6 kB]          
Obj http://es.archive.ubuntu.com precise-backports Release                     
Obj http://es.archive.ubuntu.com precise/main Sources                          
Obj http://es.archive.ubuntu.com precise/restricted Sources                    
Obj http://es.archive.ubuntu.com precise/universe Sources                      
Obj http://es.archive.ubuntu.com precise/multiverse Sources                    
Obj http://es.archive.ubuntu.com precise/main amd64 Packages                   
Obj http://es.archive.ubuntu.com precise/restricted amd64 Packages             
Obj http://es.archive.ubuntu.com precise/universe amd64 Packages               
Obj http://es.archive.ubuntu.com precise/multiverse amd64 Packages             
Obj http://es.archive.ubuntu.com precise/main i386 Packages                    
Obj http://es.archive.ubuntu.com precise/restricted i386 Packages
Obj http://es.archive.ubuntu.com precise/universe i386 Packages
Obj http://es.archive.ubuntu.com precise/multiverse i386 Packages
Obj http://es.archive.ubuntu.com precise/main TranslationIndex
Obj http://es.archive.ubuntu.com precise/multiverse TranslationIndex
Obj http://es.archive.ubuntu.com precise/restricted TranslationIndex
Obj http://es.archive.ubuntu.com precise/universe TranslationIndex
Bai:22 http://es.archive.ubuntu.com precise-updates/main Sources [217 kB]
Bai:23 http://es.archive.ubuntu.com precise-updates/restricted Sources [5118 B]
Bai:24 http://es.archive.ubuntu.com precise-updates/universe Sources [76,4 kB]
Bai:25 http://es.archive.ubuntu.com precise-updates/multiverse Sources [4737 B]
Bai:26 http://es.archive.ubuntu.com precise-updates/main amd64 Packages [479 kB]
Bai:27 http://es.archive.ubuntu.com precise-updates/restricted amd64 Packages [9531 B]
Bai:28 http://es.archive.ubuntu.com precise-updates/universe amd64 Packages [174 kB]
Bai:29 http://es.archive.ubuntu.com precise-updates/multiverse amd64 Packages [9425 B]
Bai:30 http://es.archive.ubuntu.com precise-updates/main i386 Packages [488 kB]
Bai:31 http://es.archive.ubuntu.com precise-updates/restricted i386 Packages [9483 B]
Bai:32 http://es.archive.ubuntu.com precise-updates/universe i386 Packages [176 kB]
Bai:33 http://es.archive.ubuntu.com precise-updates/multiverse i386 Packages [10,4 kB]
Bai:34 http://es.archive.ubuntu.com precise-updates/main TranslationIndex [3564 B]
Bai:35 http://es.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2605 B]
Bai:36 http://es.archive.ubuntu.com precise-updates/restricted TranslationIndex [2461 B]
Bai:37 http://es.archive.ubuntu.com precise-updates/universe TranslationIndex [2850 B]
Obj http://es.archive.ubuntu.com precise-backports/main Sources                
Obj http://es.archive.ubuntu.com precise-backports/restricted Sources          
Obj http://es.archive.ubuntu.com precise-backports/universe Sources            
Obj http://es.archive.ubuntu.com precise-backports/multiverse Sources          
Obj http://es.archive.ubuntu.com precise-backports/main amd64 Packages         
Obj http://es.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Obj http://es.archive.ubuntu.com precise-backports/universe amd64 Packages     
Obj http://es.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Obj http://es.archive.ubuntu.com precise-backports/main i386 Packages          
Obj http://es.archive.ubuntu.com precise-backports/restricted i386 Packages    
Obj http://es.archive.ubuntu.com precise-backports/universe i386 Packages      
Obj http://es.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Obj http://es.archive.ubuntu.com precise-backports/main TranslationIndex
Obj http://es.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Obj http://es.archive.ubuntu.com precise-backports/restricted TranslationIndex
Obj http://es.archive.ubuntu.com precise-backports/universe TranslationIndex
Obj http://es.archive.ubuntu.com precise/main Translation-ca
Obj http://es.archive.ubuntu.com precise/main Translation-en
Obj http://es.archive.ubuntu.com precise/multiverse Translation-ca
Obj http://es.archive.ubuntu.com precise/multiverse Translation-en
Obj http://es.archive.ubuntu.com precise/restricted Translation-ca
Obj http://es.archive.ubuntu.com precise/restricted Translation-en
Obj http://es.archive.ubuntu.com precise/universe Translation-ca
Obj http://es.archive.ubuntu.com precise/universe Translation-en
Obj http://es.archive.ubuntu.com precise-updates/main Translation-ca
Bai:38 http://es.archive.ubuntu.com precise-updates/main Translation-en [233 kB]
Obj http://es.archive.ubuntu.com precise-updates/multiverse Translation-ca     
Obj http://es.archive.ubuntu.com precise-updates/multiverse Translation-en     
Obj http://es.archive.ubuntu.com precise-updates/restricted Translation-ca     
Obj http://es.archive.ubuntu.com precise-updates/restricted Translation-en     
Obj http://es.archive.ubuntu.com precise-updates/universe Translation-ca       
Obj http://es.archive.ubuntu.com precise-updates/universe Translation-en       
Obj http://es.archive.ubuntu.com precise-backports/main Translation-en         
Obj http://es.archive.ubuntu.com precise-backports/multiverse Translation-en   
Obj http://es.archive.ubuntu.com precise-backports/restricted Translation-en   
Obj http://es.archive.ubuntu.com precise-backports/universe Translation-en     
S'ha baixat 2676 kB en 1min 33s (28,6 kB/s)                                    
S'està llegint la llista de paquets… Fet8%

```

When I enter sudo apt-get upgrade:

```
S'està llegint la llista de paquets… Fet 0%
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat… Fet%
S'actualitzaran els paquets següents:
  initramfs-tools initramfs-tools-bin jockey-common jockey-gtk libplymouth2
  linux-generic linux-image-generic plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text
11 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 0 no actualitzats.
4 no insta&#320;lats o suprimits completament.
S'ha d'obtenir 446 kB/451 kB d'arxius.
Després d'aquesta operació s'empraran 5120 B d'espai en disc addicional.
Voleu continuar [S/n]? s
Bai:1 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main initramfs-tools all 0.99ubuntu13.1 [49,0 kB]
Bai:2 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main initramfs-tools-bin amd64 0.99ubuntu13.1 [10,0 kB]
Bai:3 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main plymouth-label amd64 0.8.2-2ubuntu31 [5534 B]
Bai:4 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main plymouth amd64 0.8.2-2ubuntu31 [124 kB]
Bai:5 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main libplymouth2 amd64 0.8.2-2ubuntu31 [91,5 kB]
Bai:6 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main plymouth-theme-ubuntu-text amd64 0.8.2-2ubuntu31 [9028 B]
Bai:7 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main jockey-gtk all 0.9.7-0ubuntu7.7 [9114 B]
Bai:8 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main jockey-common all 0.9.7-0ubuntu7.7 [128 kB]
Bai:9 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main plymouth-theme-ubuntu-logo amd64 0.8.2-2ubuntu31 [19,9 kB]
S'ha baixat 446 kB en 2s (167 kB/s)              
(S'està llegint la base de dades… hi ha 294638 fitxers i directoris insta&#320;lats actualment.)
S'està preparant per a reemplaçar initramfs-tools 0.99ubuntu13 (fent servir …/initramfs-tools_0.99ubuntu13.1_all.deb)…
S'està desempaquetant el reemplaçament de initramfs-tools…
S'està preparant per a reemplaçar initramfs-tools-bin 0.99ubuntu13 (fent servir …/initramfs-tools-bin_0.99ubuntu13.1_amd64.deb)…
S'està desempaquetant el reemplaçament de initramfs-tools-bin…
S'està preparant per a reemplaçar plymouth-label 0.8.2-2ubuntu30 (fent servir …/plymouth-label_0.8.2-2ubuntu31_amd64.deb)…
S'està desempaquetant el reemplaçament de plymouth-label…
S'està preparant per a reemplaçar plymouth 0.8.2-2ubuntu30 (fent servir …/plymouth_0.8.2-2ubuntu31_amd64.deb)…
S'està desempaquetant el reemplaçament de plymouth…
S'està preparant per a reemplaçar libplymouth2 0.8.2-2ubuntu30 (fent servir …/libplymouth2_0.8.2-2ubuntu31_amd64.deb)…
S'està desempaquetant el reemplaçament de libplymouth2…
S'està preparant per a reemplaçar plymouth-theme-ubuntu-text 0.8.2-2ubuntu30 (fent servir …/plymouth-theme-ubuntu-text_0.8.2-2ubuntu31_amd64.deb)…
S'està desempaquetant el reemplaçament de plymouth-theme-ubuntu-text…
S'està preparant per a reemplaçar jockey-gtk 0.9.7-0ubuntu7.4 (fent servir …/jockey-gtk_0.9.7-0ubuntu7.7_all.deb)…
S'està desempaquetant el reemplaçament de jockey-gtk…
S'està preparant per a reemplaçar jockey-common 0.9.7-0ubuntu7.4 (fent servir …/jockey-common_0.9.7-0ubuntu7.7_all.deb)…
S'està desempaquetant el reemplaçament de jockey-common…
S'està preparant per a reemplaçar plymouth-theme-ubuntu-logo 0.8.2-2ubuntu30 (fent servir …/plymouth-theme-ubuntu-logo_0.8.2-2ubuntu31_amd64.deb)…
S'està desempaquetant el reemplaçament de plymouth-theme-ubuntu-logo…
S'estan processant els activadors per a doc-base…
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
S'estan processant els activadors per a man-db…
S'estan processant els activadors per a ureadahead…
ureadahead will be reprofiled on next reboot
S'estan processant els activadors per a bamfdaemon…
Rebuilding /usr/share/applications/bamf.index...
S'estan processant els activadors per a desktop-file-utils…
S'estan processant els activadors per a gnome-menus…
S'estan processant els activadors per a hicolor-icon-theme…
S'està configurant initramfs-tools-bin (0.99ubuntu13.1)…
S'està configurant initramfs-tools (0.99ubuntu13.1)…
update-initramfs: deferring update (trigger activated)
S'està configurant linux-image-3.2.0-35-generic (3.2.0-35.55)…
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: If: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic.postinst line 1010.
dpkg: s'ha produït un error en processar linux-image-3.2.0-35-generic (--configure):
 el subprocés s'ha insta&#320;lat el script post-installation retornà el codi d'eixida d'error 2
S'està configurant linux-image-3.2.0-36-generic (3.2.0-36.57)…
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: If: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-36-generic.postinst line 1010.
dpkg: s'ha produït un error en processar linux-image-3.2.0-36-generic (--configure):
 el subprocés s'ha insta&#320;lat el script post-installation retornà el codi d'eixida d'error 2
dpkg: problemes de dependències impedeixen la configuració de linux-image-generic:
 linux-image-generic depèn de linux-image-3.2.0-35-generic; tot i així:
  El paquet linux-image-3.2.0-35-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-image-generic (--configure):
 problemes de dependències - es deixa sense configurar
dpkg: problemes de dependències impedeixen la configuració de linux-generic:
 linux-generic depèn de linux-image-generic (= 3.2.0.35.40); tot i així:
  El paquet linux-image-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-generic (--configure):
 problemes de dependències - es deixa sense configurar
S'està configurant libplymouth2 (0.8.2-2ubuntu31)…
No s'ha escrit cap informe perquè el missatge d'error indica que és un error consequent de una fallida anterior.
                                No s'ha escrit cap informe perquè ja s'ha superat MaxReports
            S'està configurant plymouth (0.8.2-2ubuntu31)…
update-initramfs: deferring update (trigger activated)
S'està configurant plymouth-label (0.8.2-2ubuntu31)…
S'està configurant plymouth-theme-ubuntu-text (0.8.2-2ubuntu31)…
update-initramfs: deferring update (trigger activated)
S'està configurant jockey-common (0.9.7-0ubuntu7.7)…
S'està configurant jockey-gtk (0.9.7-0ubuntu7.7)…
S'està configurant plymouth-theme-ubuntu-logo (0.8.2-2ubuntu31)…
update-initramfs: deferring update (trigger activated)
S'estan processant els activadors per a initramfs-tools…
update-initramfs: Generating /boot/initrd.img-3.2.0-36-generic
S'estan processant els activadors per a libc-bin…
ldconfig deferred processing now taking place
S'han trobat errors en processar:
 linux-image-3.2.0-35-generic
 linux-image-3.2.0-36-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I enter sudo apt-get dist-upgrade:

```
S'està llegint la llista de paquets… Fet%
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat… Fet%
S'està calculant l'actualització… Fet
S'actualitzaran els paquets següents:
  linux-generic linux-image-generic
2 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 0 no actualitzats.
4 no insta&#320;lats o suprimits completament.
S'ha d'obtenir 0 B/4400 B d'arxius.
Després d'aquesta operació s'empraran 0 B d'espai en disc addicional.
Voleu continuar [S/n]? s
S'està configurant linux-image-3.2.0-35-generic (3.2.0-35.55)…
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: If: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic.postinst line 1010.
dpkg: s'ha produït un error en processar linux-image-3.2.0-35-generic (--configure):
 el subprocés s'ha insta&#320;lat el script post-installation retornà el codi d'eixida d'error 2
S'està configurant linux-image-3.2.0-36-generic (3.2.0-36.57)…
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: If: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-36-generic.postinst line 1010.
dpkg: s'ha produït un error en processar linux-image-3.2.0-36-generic (--configure):
 el subprocés s'ha insta&#320;lat el script post-installation retornà el codi d'eixida d'error 2
dpkg: problemes de dependències impedeixen la configuració de linux-image-generic:
 linux-image-generic depèn de linux-image-3.2.0-35-generic; tot i així:
  El paquet linux-image-3.2.0-35-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-image-generic (--configure):
 problemes de dependències - es deixa sense configurar
dpkg: problemes de dependències impedeixen la configuració de linux-generic:
 linux-generic depèn de linux-image-generic (= 3.2.0.35.40); tot i així:
  El paquet linux-image-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-generic (--configure):
 problemes de dependències - es deixa sense configurar
No s'ha escrit cap informe perquè el missatge d'error indica que és un error consequent de una fallida anterior.
                                No s'ha escrit cap informe perquè ja s'ha superat MaxReports
            S'han trobat errors en processar:
 linux-image-3.2.0-35-generic
 linux-image-3.2.0-36-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thank you for helping.

---

### Post by Cheesehead on 2013-01-30
> **fleneh said:**
> 
update-initramfs: deferring update (trigger activated)
S'està configurant linux-image-3.2.0-35-generic (3.2.0-35.55)…
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-35-generic /boot/vmlinuz-3.2.0-35-generic
[COLOR="Red"]**/usr/sbin/grub-mkconfig: 1: /etc/default/grub: If: not found**[/COLOR]
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic.postinst line 1010.
dpkg: s'ha produït un error en processar linux-image-3.2.0-35-generic (--configure):
 el subprocés s'ha insta&#320;lat el script post-installation retornà el codi d'eixida d'error 2
S'està configurant linux-image-3.2.0-36-generic (3.2.0-36.57)…
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic


There seems to be a typo in your /usr/sbin/grub-mkconfig file.
The first few lines should look like: ```
#! /bin/sh
set -e

# Generate grub.cfg by inspecting /boot contents.
# Copyright (C) 2006,2007,2008,2009,2010 Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

transform="s,x,x,"
prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"

prefix="/usr"
exec_prefix="${prefix}"

```
If yours looks different, how different? A simple typo can be fixed. Or the whole file can be manually replaced. Or the entire package can be reinstalled.

---

### Post by fleneh on 2013-01-30
Hi Cheesehead. This is the hole /usr/sbin/grub-mkonfig file:

```
#! /bin/sh
set -e

# Generate grub.cfg by inspecting /boot contents.
# Copyright (C) 2006,2007,2008,2009,2010 Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

transform="s,x,x,"
prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"

prefix="/usr"
exec_prefix="${prefix}"
sbindir="${exec_prefix}/sbin"
bindir="${exec_prefix}/bin"
sysconfdir="/etc"
PACKAGE_NAME=GRUB
PACKAGE_VERSION=1.99-21ubuntu3.7
host_os=linux-gnu
datadir="${datarootdir}"
pkgdatadir="${datadir}/`echo grub | sed "${transform}"`"
grub_cfg=""
grub_mkconfig_dir="${sysconfdir}"/grub.d

self=`basename $0`

grub_probe="${sbindir}/`echo grub-probe | sed "${transform}"`"
grub_script_check="${bindir}/`echo grub-script-check | sed "${transform}"`"

GRUB_PREFIX=`echo '/boot/grub' | sed "s,//*,/,g"`

# Usage: usage
# Print the usage.
usage () {
    cat <<EOF
Usage: $self [OPTION]
Generate a grub config file

  -o, --output=FILE       output generated config to FILE [default=stdout]
  -h, --help              print this message and exit
  -v, --version           print the version information and exit

Report bugs to <bug-grub@gnu.org>.
EOF
}

argument () {
  opt=$1
  shift

  if test $# -eq 0; then
      echo "$0: option requires an argument -- '$opt'" 1>&2
      exit 1
  fi
  echo $1
}

# Check the arguments.
while test $# -gt 0
do
    option=$1
    shift

    case "$option" in
    -h | --help)
	usage
	exit 0 ;;
    -v | --version)
	echo "$self (${PACKAGE_NAME}) ${PACKAGE_VERSION}"
	exit 0 ;;
    -o | --output)
	grub_cfg=`argument $option "$@"`; shift;;
    --output=*)
	grub_cfg=`echo "$option" | sed 's/--output=//'`
	;;
    -*)
	echo "Unrecognized option \`$option'" 1>&2
	usage
	exit 1
	;;
    # Explicitly ignore non-option arguments, for compatibility.
    esac
done

. "${datadir}/grub/grub-mkconfig_lib"

if [ "x$EUID" = "x" ] ; then
  EUID=`id -u`
fi

if [ "$EUID" != 0 ] ; then
  root=f
  case "`uname 2>/dev/null`" in
    CYGWIN*)
      # Cygwin: Assume root if member of admin group
      for g in `id -G 2>/dev/null` ; do
	case $g in
	  0|544) root=t ;;
	esac
      done ;;
  esac
  if [ $root != t ] ; then
    echo "$self: You must run this as root" >&2
    exit 1
  fi
fi

set $grub_probe dummy
if test -f "$1"; then
    :
else
    echo "$1: Not found." 1>&2
    exit 1
fi

mkdir -p ${GRUB_PREFIX}

# Device containing our userland.  Typically used for root= parameter.
GRUB_DEVICE="`${grub_probe} --target=device /`"
GRUB_DEVICE_UUID="`${grub_probe} --device ${GRUB_DEVICE} --target=fs_uuid 2> /dev/null`" || true

# Device containing our /boot partition.  Usually the same as GRUB_DEVICE.
GRUB_DEVICE_BOOT="`${grub_probe} --target=device /boot`"
GRUB_DEVICE_BOOT_UUID="`${grub_probe} --device ${GRUB_DEVICE_BOOT} --target=fs_uuid 2> /dev/null`" || true

# Filesystem for the device containing our userland.  Used for stuff like
# choosing Hurd filesystem module.
GRUB_FS="`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2> /dev/null || echo unknown`"

if test -f ${sysconfdir}/default/grub ; then
  . ${sysconfdir}/default/grub
fi

# XXX: should this be deprecated at some point?
if [ "x${GRUB_TERMINAL}" != "x" ] ; then
  GRUB_TERMINAL_INPUT="${GRUB_TERMINAL}"
  GRUB_TERMINAL_OUTPUT="${GRUB_TERMINAL}"
fi

termoutdefault=0
if [ "x${GRUB_TERMINAL_OUTPUT}" = "x" ]; then
    GRUB_TERMINAL_OUTPUT=gfxterm;
    termoutdefault=1;
fi

for x in ${GRUB_TERMINAL_OUTPUT}; do
    if [ "x${x}" = "xgfxterm" ]; then
	if [ -n "$GRUB_FONT" ] ; then
	    if is_path_readable_by_grub ${GRUB_FONT} > /dev/null ; then
		GRUB_FONT_PATH=${GRUB_FONT}
	    else
		echo "No such font or not readable by grub: ${GRUB_FONT}" >&2
		exit 1
	    fi
	else
	    for dir in ${pkgdatadir} ${GRUB_PREFIX} /usr/share/grub ; do
		for basename in unicode unifont ascii; do
		    path="${dir}/${basename}.pf2"
		    if is_path_readable_by_grub ${path} > /dev/null ; then
			GRUB_FONT_PATH=${path}
		    else
			continue
		    fi
		    if [ "${basename}" = "ascii" ] ; then
	                # make sure all our children behave in conformance with ascii..
			export LANG=C
		    fi
		    break 2
		done
	    done
	fi
	if [ -z "${GRUB_FONT_PATH}" ] ; then
	    if [ "x$termoutdefault" != "x1" ]; then
		echo "No font for gfxterm found." >&2 ; exit 1
	    fi
	    GRUB_TERMINAL_OUTPUT=
	fi
    fi
done

for x in ${GRUB_TERMINAL_OUTPUT}; do
    case "x${x}" in
	xgfxterm) ;;
	xconsole | xserial | xofconsole)
            # make sure all our children behave in conformance with ascii..
	    export LANG=C;;
	*) echo "Invalid output terminal \"${GRUB_TERMINAL_OUTPUT}\"" >&2 ; exit 1 ;;
    esac
done

# These are defined in this script, export them here so that user can
# override them.
export GRUB_DEVICE \
  GRUB_DEVICE_UUID \
  GRUB_DEVICE_BOOT \
  GRUB_DEVICE_BOOT_UUID \
  GRUB_FS \
  GRUB_FONT_PATH \
  GRUB_PRELOAD_MODULES \
  GRUB_PREFIX

# These are optional, user-defined variables.
export GRUB_DEFAULT \
  GRUB_HIDDEN_TIMEOUT \
  GRUB_HIDDEN_TIMEOUT_QUIET \
  GRUB_TIMEOUT \
  GRUB_DEFAULT_BUTTON \
  GRUB_HIDDEN_TIMEOUT_BUTTON \
  GRUB_TIMEOUT_BUTTON \
  GRUB_BUTTON_CMOS_ADDRESS \
  GRUB_BUTTON_CMOS_CLEAN \
  GRUB_DISTRIBUTOR \
  GRUB_CMDLINE_LINUX \
  GRUB_CMDLINE_LINUX_DEFAULT \
  GRUB_CMDLINE_XEN \
  GRUB_CMDLINE_XEN_DEFAULT \
  GRUB_CMDLINE_LINUX_XEN_REPLACE \
  GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT \
  GRUB_CMDLINE_NETBSD \
  GRUB_CMDLINE_NETBSD_DEFAULT \
  GRUB_CMDLINE_GNUMACH \
  GRUB_TERMINAL_INPUT \
  GRUB_TERMINAL_OUTPUT \
  GRUB_SERIAL_COMMAND \
  GRUB_DISABLE_LINUX_UUID \
  GRUB_DISABLE_RECOVERY \
  GRUB_VIDEO_BACKEND \
  GRUB_GFXMODE \
  GRUB_BACKGROUND \
  GRUB_THEME \
  GRUB_GFXPAYLOAD_LINUX \
  GRUB_DISABLE_OS_PROBER \
  GRUB_INIT_TUNE \
  GRUB_SAVEDEFAULT \
  GRUB_BADRAM \
  GRUB_RECORDFAIL_TIMEOUT

if test "x${grub_cfg}" != "x"; then
  rm -f ${grub_cfg}.new
  exec > ${grub_cfg}.new

  # Allow this to fail, since /boot/grub/ might need to be fatfs to support some
  # firmware implementations (e.g. OFW or EFI).
  chmod 400 ${grub_cfg}.new || grub_warn "Could not make ${grub_cfg}.new readable by only root.\
  This means that if the generated config contains a password it is readable by everyone"
fi
echo "Generating grub.cfg ..." >&2

cat << EOF
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by $self using templates
# from ${grub_mkconfig_dir} and settings from ${sysconfdir}/default/grub
#
EOF

for i in ${grub_mkconfig_dir}/* ; do
  case "$i" in
    # emacsen backup files. FIXME: support other editors
    *~) ;;
    # emacsen autosave files. FIXME: support other editors
    \#*\#) ;;
    *)
      if grub_file_is_not_garbage "$i" && test -x "$i" ; then
        echo
        echo "### BEGIN $i ###"
        "$i"
        echo "### END $i ###"
      fi
    ;;
  esac
done

if [ "x${grub_cfg}" != "x" ] && ! grep "^password " ${grub_cfg}.new >/dev/null; then
  chmod 444 ${grub_cfg}.new || true
fi

if test "x${grub_cfg}" != "x" ; then
  if ! ${grub_script_check} ${grub_cfg}.new; then
    echo "Syntax errors are detected in generated GRUB config file." >&2
    echo "Ensure that there are no errors in /etc/default/grub" >&2
    echo "and /etc/grub.d/* files or please file a bug report with" >&2
    echo "${grub_cfg}.new file attached." >&2
  else
    # none of the children aborted with error, install the new grub.cfg
    mv -f ${grub_cfg}.new ${grub_cfg}
  fi
fi

echo "done" >&2

```

---

### Post by steeldriver on 2013-01-30
... or maybe a # (comment marker) gone missing from the top of your /etc/default/grub file?

```
$ head /etc/default/grub
[COLOR=Red]**# If**[/COLOR] you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

```

---

### Post by fleneh on 2013-01-30
This is the header of /etc/default/grub file: 
```
 If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
GRUB_CMDLINE_LINUX=""
```

There is a missing # in the top of the file. How can I change and save it?
Thanks

---

### Post by steeldriver on 2013-01-30
GUI:

```
gksudo gedit /etc/default/grub
```Command line

```
sudo nano  /etc/default/grub
```then just type in the missing # , save and quit

Or you could just run this one-liner 

```
sudo sed -i '1 s/.*/#&/' /etc/default/grub
```

---

### Post by dino99 on 2013-01-30
hey, what have you done there ?
- i'm seeing both i386 & amd64 repo
- grub installation is borked

so i'm afraid you need to clarify yourself what you want : 32 or 64 bits installation ?

please post here the output of :    cat /etc/apt/sources.list

---

### Post by fleneh on 2013-01-30
I could update now without any error. There was just a # missing on the top of /etc/default/grub file. I don't know how I had changed it.
Thank you very much indeed.

dino99, this is the output of cat /etc/apt/sources.list: I have 64bits

```
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://es.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://es.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://es.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://es.archive.ubuntu.com/ubuntu/ precise universe
deb http://es.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://es.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://es.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://es.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://es.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://repository.spotify.com stable non-free

```

---

### Post by dino99 on 2013-01-30
so you have updated grub again ? (sudo update-grub)

thats good you can update again, you're sources are clean. (i was disturbed by the spotify i386 above)

note: as this problem is now fixed, please set that thread as SOLVED using the top right Thread Tools menu.

---

### Post by fleneh on 2013-01-30
Yes I could update.
Thank you, I will add [solved] to this post.

---

