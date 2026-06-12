---
title: "Broken package showing message: E: Sub-process /usr/bin/dpkg returned an error"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by Unkuiri on 2012-05-30
Hi, Any time I install a new package or update it shows me this message:
> update-alternatives: erro: argumento desconhecido `boot'
dpkg: erro ao processar oracle-java7-installer (--remove):
 subprocesso script pre-removal instalado retornou erro do status de saída 2
Downloading...
--2012-05-30 15:13:46--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
A resolver download.oracle.com... 194.65.2.17, 194.65.2.42
A conectar download.oracle.com|194.65.2.17|:80... conectado.
Pedido HTTP enviado, a aguardar resposta... 302 Moved Temporarily
Localização: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [a seguir]
--2012-05-30 15:13:46--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
A resolver edelivery.oracle.com... 2.17.250.174
A conectar edelivery.oracle.com|2.17.250.174|:443... conectado.
Pedido HTTP enviado, a aguardar resposta... 302 Moved Temporarily
Localização: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [a seguir]
--2012-05-30 15:13:47--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
A conectar download.oracle.com|194.65.2.17|:80... conectado.
Pedido HTTP enviado, a aguardar resposta... 200 OK
Tamanho: 5307 (5,2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 1,39M=0,004s

2012-05-30 15:13:47 (1,39 MB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: erro enquanto limpava:
 subprocesso script post-installation instalado retornou erro do status de saída 1
A remover iw ...
A processar 'triggers' para man-db ...
Foram encontrados erros enquanto processava:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried to install oracle java 7 from a launchpad source and it gave error, now I've installed it from other source without problems but the error keeps showing and I can't remove the package.

How can I solve this?

Thanks in advance

P.S.:I'm using ubuntu oneiric

---

### Post by zvacet on 2012-05-30
Try with 

```
sudo dpkg --configure -a
```

---

### Post by Unkuiri on 2012-05-30
I tried it already but it continues to show this message when I try to remove the file...

---

### Post by raja.genupula on 2012-05-30
hi 
could you give me the output of 

```
sudo apt-get update
```

---

### Post by Unkuiri on 2012-05-30
The output of "sudo apt-get update":

> Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                                                                                    
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric InRelease                                                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                                                                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease                                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                                                                                          
Obter:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                                                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                    
Obter:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                                                                                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                                                                                                                                   
Obter:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg [198 B]                                                                                  
Obter:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg [198 B]                                                                              
Obter:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg [198 B]                                                                            
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs InRelease                                                                                                          
Obter:6 [http://dl.google.com](http://dl.google.com) stable Release [1349 B]                                                                                         
Obter:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg [198 B]                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                                              
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main i386 Packages                                                                                                                     
Obter:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release [40,8 kB]                                                                                                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                                                                                                                                
Obter:9 [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release.gpg [490 B]                                                                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                                                    
Obter:10 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [639 B]                                                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                                                                                                                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                                                                                             
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main TranslationIndex                                                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                                                                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                                                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                                                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                                                                                                         
Obter:11 [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release [2870 B]                                                                                                                                                
Obter:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release [40,8 kB]                                                                                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                                                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                                                                                    
Obter:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release [40,8 kB]                                                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                                                                                                                
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release                                                                                                           
Obter:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release [40,8 kB]                                                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                               
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                                                                                 
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all i386 Packages/DiffIndex                                                                                                                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                                                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                              
Obter:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources [877 kB]                                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                              
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all TranslationIndex                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                               
Obter:16 [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all i386 Packages [1335 B]                                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                                                                                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                                                                                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-pt_PT                                                                                           
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main Translation-pt_PT                                                                                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-pt                                                                                              
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main Translation-pt                                                                                                                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                                                                                                                           
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) oneiric/main Translation-en                                                                                                             
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all Translation-pt_PT                                                                                                                  
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all Translation-pt                                                                       
Ign [http://www.duinsoft.nl](http://www.duinsoft.nl) debs/all Translation-en                                          
Obter:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources [5351 B]                      
Obter:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources [4677 kB]                                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT                                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt_PT     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-pt        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-pt_PT           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-pt              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Obter:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources [149 kB]                                                                                                                                                                       
Obter:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages [1226 kB]                                                                                                                                                                      
Obter:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages [8216 B]                                                                                                                                                                 
Obter:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages [4468 kB]                                                                                                                                                                  
Obter:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages [119 kB]                                                                                                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                                                                                                                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex                                                                                                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex                                                                                                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex                                                                                                                                                                              
Obter:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources [142 kB]                                                                                                                                                                     
Obter:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources [3347 B]                                                                                                                                                               
Obter:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources [54,5 kB]                                                                                                                                                                
Obter:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources [3660 B]                                                                                                                                                               
Obter:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages [353 kB]                                                                                                                                                               
Obter:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages [6631 B]                                                                                                                                                         
Obter:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages [116 kB]                                                                                                                                                           
Obter:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6363 B]                                                                                                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex                                                                                                                                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex                                                                                                                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex                                                                                                                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex                                                                                                                                                                      
Obter:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Sources [2742 B]                                                                                                                                                                   
Obter:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Sources [14 B]                                                                                                                                                               
Obter:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Sources [9019 B]                                                                                                                                                               
Obter:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Sources [14 B]                                                                                                                                                               
Obter:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main i386 Packages [3296 B]                                                                                                                                                             
Obter:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted i386 Packages [14 B]                                                                                                                                                         
Obter:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe i386 Packages [13,4 kB]                                                                                                                                                        
Obter:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse i386 Packages [14 B]                                                                                                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main TranslationIndex                                                                                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex                                                                                                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted TranslationIndex                                                                                                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe TranslationIndex                                                                                                                                                                    
Obter:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources [37,8 kB]                                                                                                                                                                   
Obter:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources [1959 B]                                                                                                                                                              
Obter:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources [17,3 kB]                                                                                                                                                               
Obter:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources [1644 B]                                                                                                                                                              
Obter:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages [121 kB]                                                                                                                                                              
Obter:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages [3939 B]                                                                                                                                                        
Obter:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages [37,3 kB]                                                                                                                                                         
Obter:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages [3371 B]                                                                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex                                                                                                                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex                                                                                                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex                                                                                                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex                                                                                                                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-pt                                                                                                                                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en                                                                                                                                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-pt                                                                                                                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en                                                                                                                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-pt                                                                                                                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en                                                                                                                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-pt                                                                                                                                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en                                                                                                                                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en                                                                                                                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en                                                                                                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en                                                                                                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en                                                                                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Translation-en                                                                                                                                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Translation-en                                                                                                                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Translation-en                                                                                                                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Translation-en                                                                                                                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en                                                                                                                                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en                                                                                                                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en                                                                                                                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en                                                                                                                                                                       
Obtidos 12,6 MB em 24s (525 kB/s)                                                                                                                                                                                                            
A ler as listas de pacotes... Pronto
W: Erro GPG: [http://www.duinsoft.nl](http://www.duinsoft.nl) debs Release: As seguintes assinaturas não puderam ser verificadas porque a chave pública não está disponível: NO_PUBKEY E18CE6625CB26B26

---

### Post by raja.genupula on 2012-05-31
```
**sha256sum mismatch jdk-7u3-linux-i586.tar.gz**
Oracle JDK 7 is NOT installed.
dpkg: erro enquanto limpava:
 subprocesso script post-installation instalado retornou erro do status de saída 1
```

I am thinking about the bold line . 

ok try this
```
sudo -i
apt-get autoclean
apt-get autoremove
apt-get update
apt-get upgrade ;apt-get dist-upgrade
```

try that one and tell me what you got .

---

### Post by Unkuiri on 2012-05-31
I tried what you sugested, the result is here:
[http://paste.ubuntu.com/1016105/]("http://paste.ubuntu.com/1016105/")
still not working...

---

