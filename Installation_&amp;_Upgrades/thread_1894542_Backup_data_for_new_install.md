---
title: "Backup data for new install"
date: 2011-12-12
forum: Installation &amp; Upgrades
---

### Post by yoramdavid on 2011-12-12
Hello all,

I am having many problems with my ubuntu 11.10, did a backup which helped with some problems but brought others.
I am where I cannot download programs too big in MB.

I do have a pen-drive with  Ubuntu 10.04 installation. 
If my Ubuntu stops responding at all and I do a fresh install of 10.04, can I make a backup of all the installed programs to use later on 10.04?
And all my settings such as firefox plugins, addons, Thunderbird?

Thank you,

Yoram

---

### Post by jerrrys on 2011-12-14
If you wish to attempt a fix for your 11.10 problem, open a terminal and

sudo apt-get update

and post any errors.

There must be a hundred ways to backup

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup&as_qdr=all&sa=Google+Search&lang=en)

But sounds like you may be a good candidate for a separate home folder 

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=separate+home+folder+&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=separate+home+folder+&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by yoramdavid on 2011-12-14
> **jerrrys said:**
> If you wish to attempt a fix for your 11.10 problem, open a terminal and

sudo apt-get update

and post any errors.

There must be a hundred ways to backup

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup&as_qdr=all&sa=Google+Search&lang=en)

But sounds like you may be a good candidate for a separate home folder 

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=separate+home+folder+&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=separate+home+folder+&as_qdr=all&sa=Google+Search&lang=en)

Thank  you jerrrys,

I will post the results of the above comman when it finishes (it always takes a long time, when it reaches 99%[waiting for headers])
M question was more about can I backup my installed programs in ubuntu 11.10 and then use them in Ubuntu 10.04?

---

### Post by yoramdavid on 2011-12-14
> **jerrrys said:**
> If you wish to attempt a fix for your 11.10 problem, open a terminal and

sudo apt-get update

and post any errors.


Here is the result:
```
yoram@yoram-II:~$ sudo apt-get update
[sudo] password for yoram: 
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://ppa.launchpad.net karmic InRelease                                  
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net maverick InRelease                                
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://download.bitdefender.com bitdefender InRelease                      
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net karmic Release.gpg                                
Obter:1 http://ppa.launchpad.net oneiric Release.gpg [316 B]                   
Ign http://ppa.launchpad.net maverick Release.gpg                              
Obter:2 http://ppa.launchpad.net oneiric Release.gpg [316 B]                   
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Obter:3 http://download.bitdefender.com bitdefender Release.gpg [197 B]        
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://archive.ubuntu.com oneiric-updates Release.gpg                      
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Obter:4 http://ppa.launchpad.net oneiric Release.gpg [316 B]                   
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Obter:5 http://ppa.launchpad.net oneiric Release.gpg [316 B]                   
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Obter:6 http://ppa.launchpad.net oneiric Release [9757 B]                      
Ign http://ppa.launchpad.net maverick Release                                  
Err http://ppa.launchpad.net oneiric Release                                   
  
Hit http://download.bitdefender.com bitdefender Release                        
Ign http://download.bitdefender.com bitdefender Release                        
Hit http://archive.ubuntu.com oneiric Release                                  
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.ubuntu.com oneiric-updates Release                          
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net maverick/main TranslationIndex                    
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages                  
Hit http://archive.ubuntu.com oneiric/main amd64 Packages                      
Hit http://archive.ubuntu.com oneiric/restricted amd64 Packages                
Hit http://archive.ubuntu.com oneiric/multiverse amd64 Packages                
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages                 
Hit http://archive.ubuntu.com oneiric/main TranslationIndex                    
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net oneiric/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex              
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex                
Hit http://archive.ubuntu.com oneiric-updates/universe amd64 Packages          
Hit http://archive.ubuntu.com oneiric-updates/main amd64 Packages              
Hit http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages        
Hit http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages        
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages           
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages               
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages         
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex            
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex        
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric/main Translation-pt                      
Hit http://archive.ubuntu.com oneiric/main Translation-en                      
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Ign http://download.bitdefender.com bitdefender/non-free Sources/DiffIndex     
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric/multiverse Translation-pt                
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en                
Hit http://archive.ubuntu.com oneiric/restricted Translation-pt                
Hit http://archive.ubuntu.com oneiric/restricted Translation-en                
Hit http://archive.ubuntu.com oneiric/universe Translation-pt                  
Hit http://archive.ubuntu.com oneiric/universe Translation-en                  
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en              
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en        
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en          
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://download.bitdefender.com bitdefender/non-free amd64 Packages/DiffIndex
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign http://download.bitdefender.com bitdefender/non-free i386 Packages/DiffIndex
Ign http://download.bitdefender.com bitdefender/non-free TranslationIndex      
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex                    
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Ign http://ppa.launchpad.net oneiric/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net oneiric/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages     
Hit http://ppa.launchpad.net oneiric/main i386 Packages      
Hit http://ppa.launchpad.net oneiric/main Sources                             
Hit http://ppa.launchpad.net oneiric/main amd64 Packages     
Hit http://ppa.launchpad.net oneiric/main i386 Packages      
Hit http://ppa.launchpad.net oneiric/main Sources            
Hit http://download.bitdefender.com bitdefender/non-free Sources
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://download.bitdefender.com bitdefender/non-free amd64 Packages        
Hit http://download.bitdefender.com bitdefender/non-free i386 Packages         
Ign http://download.bitdefender.com bitdefender/non-free Translation-pt_PT     
Ign http://download.bitdefender.com bitdefender/non-free Translation-pt
Ign http://download.bitdefender.com bitdefender/non-free Translation-en
Err http://ppa.launchpad.net maverick/main Sources           
  404  Not Found
Err http://ppa.launchpad.net maverick/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net maverick/main Translation-pt_PT
Ign http://ppa.launchpad.net maverick/main Translation-pt
Ign http://ppa.launchpad.net maverick/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-pt_PT
Ign http://ppa.launchpad.net oneiric/main Translation-pt
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-pt_PT
Ign http://ppa.launchpad.net oneiric/main Translation-pt
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-pt_PT
Ign http://ppa.launchpad.net oneiric/main Translation-pt
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-pt_PT
Ign http://ppa.launchpad.net oneiric/main Translation-pt
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-pt_PT
Ign http://ppa.launchpad.net oneiric/main Translation-pt
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-pt_PT
Ign http://ppa.launchpad.net oneiric/main Translation-pt
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-pt_PT
Ign http://ppa.launchpad.net oneiric/main Translation-pt
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-pt_PT
Ign http://ppa.launchpad.net oneiric/main Translation-pt
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-pt_PT
Ign http://ppa.launchpad.net oneiric/main Translation-pt
Ign http://ppa.launchpad.net oneiric/main Translation-en
Obtidos 1462 B em 1min 6s (22 B/s)
A ler as listas de pacotes... Pronto
W: Ocorreu um erro durante a verificação da assinatura. O repositório não está actualizado e serão utilizados os ficheiros anteriores de índice. Erro do GPG: http://ppa.launchpad.net oneiric Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY 95FABEFB4499973B

W: Erro GPG: http://download.bitdefender.com bitdefender Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY A373FB480EC4FE05
W: Erro GPG: http://ppa.launchpad.net oneiric Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY D702BF6B8C6C1EFD
W: Erro GPG: http://ppa.launchpad.net oneiric Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY 6AF0E1940624A220
W: Erro GPG: http://ppa.launchpad.net oneiric Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY 32B18A1260D8DA0B
W: Falhou obter http://ppa.launchpad.net/listen-devel/ppa/ubuntu/dists/karmic/Release  Unable to find expected entry 'main./source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Falhou obter http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu/dists/oneiric/Release  

W: Falhou obter http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/maverick/main/source/Sources  404  Not Found

W: Falhou obter http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/maverick/main/binary-amd64/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/bean123ch/bur/ubuntu/dists/maverick/main/binary-i386/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Falhou obter http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/dockbar-main/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Falhou obter http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Falhou obter http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Falhou obter http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Falhou obter http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

