---
title: "upgrade feisty problems"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by flikmax on 2007-07-18
hi all, i've a problem to upgrading my ubuntu feisty.. i've just finish to install it and i tryied to upgrade it via synaptic but i receive some error from italian language packs, python 2.5 pack and some others ...

packets result corrupted so i cant install or patching anything!! 

the are some logs by shell:

1. after digit sudo apt-get -f install (to try resolve problems):

> Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Reading state information... Fatto               
Correzione delle dipendenze in corso... Fatto
I seguenti pacchetti verranno inoltre installati:
  language-pack-gnome-it-base
Pacchetti raccomandati:
  language-support-it
I seguenti pacchetti NUOVI (NEW) saranno installati:
  language-pack-gnome-it-base
0 aggiornati, 1 installati, 0 da rimuovere e 92 non aggiornati.
1 non completamente installati o rimossi.
È necessario prendere 0B/1353kB di archivi. 
Dopo l'estrazione, verranno occupati 4948kB di spazio su disco.
Continuare [S/n]? 
(Lettura del database ... 88040 file e directory attualmente installati.)
Spacchetto language-pack-gnome-it-base (da .../language-pack-gnome-it-base_1%3a7.04+20070412_all.deb) ...
Sostituiti dai file nel pacchetto installato language-pack-gnome-it ...
dpkg: errore processando /var/cache/apt/archives/language-pack-gnome-it-base_1%3a7.04+20070412_all.deb (--unpack):
 il file tar è rovinato - l'archivio del pacchetto è rovinato
dpkg-deb: il sottoprocesso paste è stato terminato dal segnale (Broken pipe)
Sono occorsi degli errori processando:
 /var/cache/apt/archives/language-pack-gnome-it-base_1%3a7.04+20070412_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



after doing sudo apt-get update:

> Get:1 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty Release.gpg [191B]
Get:2 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/main Translation-it [50,6kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-it   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-it
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-it
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-it
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:4 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/restricted Translation-it [14B]
Get:5 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/universe Translation-it [43,8kB]
Get:6 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/multiverse Translation-it [707B]     
Get:7 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates Release.gpg [191B]        
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/main Translation-it
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/restricted Translation-it
Get:8 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports Release.gpg [191B]         
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/main Translation-it          
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/restricted Translation-it    
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/universe Translation-it      
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/multiverse Translation-it    
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty Release                                
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/restricted Sources
Get:9 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/universe Packages [3754kB]
Get:10 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/universe Sources [1131kB]           
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-updates/restricted Sources             
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/main Packages                
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/restricted Packages          
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/universe Packages            
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/multiverse Packages          
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/main Sources                 
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/restricted Sources           
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/universe Sources             
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty-backports/multiverse Sources           
Scaricato 4981kB in 11s (432kB/s)                                              
Lettura della lista dei pacchetti in corso... Fatto



after doing apt-get upgrade:

> Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Reading state information... Fatto               
È consigliabile eseguire `apt-get -f install' per correggere questi problemi.
I seguenti pacchetti hanno dipendenze non soddisfatte:
  language-pack-gnome-it: Dipende: language-pack-gnome-it-base ma non è installato
E: Dipendenze non trovate. Riprovare usando -f.


help pls! i've just tried to complete remove the language pack and reinstall it, but now there is a problem with pythn 2.5 <- it seems corrupted so i cant install anything !


thk u for support! :(

---

