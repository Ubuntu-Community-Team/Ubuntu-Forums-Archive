---
title: "can not update ubuntu 11.10"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by nobody850 on 2011-10-19
every time i try to update it gives me the error:

Requires installation of untrusted packages



The action would require the installation of packages from not authenticated sources.

details: apport-hooks-medibuntu chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg libavcodec-extra-53 libavutil-extra-51 mplayer

---

### Post by garvinrick4 on 2011-10-19
Key for medibuntu repositorys.

```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
``````
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```Chromium-browser do you have a .ppa for chromium-browser=need the key:
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)
Or google Launchpad.net ppa for chromium and install key if that is where you got your ppa from.
Here it is:   [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by nobody850 on 2011-10-19
i went to terminal then entered the first code, then the second one but still no go.

---

### Post by garvinrick4 on 2011-10-19
It will just say OK or something like that. It just gives you key for medibuntu, you installed them without key. click on screenshots.

---

### Post by nobody850 on 2011-10-19
sorry i am still new to this, here what i got in the terminal

khalid@khalid-H55M-USB3:~$ gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
gpg: directory `/home/khalid/.gnupg' created
gpg: new configuration file `/home/khalid/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/khalid/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/khalid/.gnupg/secring.gpg' created
gpg: keyring `/home/khalid/.gnupg/pubring.gpg' created
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: /home/khalid/.gnupg/trustdb.gpg: trustdb created
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
khalid@khalid-H55M-USB3:~$ gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
[sudo] password for khalid: 
OK

---

### Post by garvinrick4 on 2011-10-19
So when you run 
```
sudo apt-get update 
```
What are errors.

---

### Post by nobody850 on 2011-10-19
khalid@khalid-H55M-USB3:~$ sudo apt-get update
[sudo] password for khalid: 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty InRelease                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric InRelease                             
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports InRelease                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://linux.dropbox.com](http://linux.dropbox.com) natty Release.gpg                                 
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg [198 B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric Release.gpg                           
Get:4 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) natty Release                                     
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release [40.8 kB]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages      
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease [7,096 B]                
Hit [http://linux.dropbox.com](http://linux.dropbox.com) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages/DiffIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) natty/main i386 Packages                          
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty/main TranslationIndex                       
Get:7 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates Release [28.2 kB]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Ign [http://repository.glx-dock.org](http://repository.glx-dock.org) oneiric InRelease                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources [877 kB]                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/main amd64 Packages                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/restricted amd64 Packages             
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/universe amd64 Packages               
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/multiverse amd64 Packages             
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
  404  Not Found
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/universe TranslationIndex             
Get:9 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/restricted Sources [14 B]   
Get:10 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/main Sources [14.0 kB]     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Get:11 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/multiverse Sources [14 B]  
Get:12 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/universe Sources [1,886 B] 
Get:13 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/main amd64 Packages [27.4 kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Get:14 [http://repository.glx-dock.org](http://repository.glx-dock.org) oneiric Release.gpg [198 B]              
Get:15 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages [14 B]
Get:16 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/universe amd64 Packages [8,016 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Get:17 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages [14 B]
Get:18 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/main i386 Packages [27.5 kB]
Get:19 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [14 B]
Get:20 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/universe i386 Packages [8,016 B]
Get:21 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [14 B]
Get:22 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/main TranslationIndex [73 B]
Get:23 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [70 B]
Get:24 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [70 B]
Get:25 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [72 B]
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/restricted Sources          
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty/main Translation-en_US                      
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/main amd64 Packages         
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/universe amd64 Packages     
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty/main Translation-en                         
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric/universe Translation-en               
Get:26 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/main Translation-en [14.2 kB]
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Get:27 [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-updates/universe Translation-en [5,593 B]
Get:28 [http://repository.glx-dock.org](http://repository.glx-dock.org) oneiric Release [4,610 B]                
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources [5,351 B]          
Get:30 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Sources [3,279 B]            
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/main Translation-en_US      
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/main Translation-en         
Get:31 [http://repository.glx-dock.org](http://repository.glx-dock.org) oneiric/cairo-dock amd64 Packages [5,164 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/multiverse Translation-en_US
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Get:32 [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Sources [4,356 B]        
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/restricted Translation-en_US
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/universe Translation-en_US  
Ign [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) oneiric-backports/universe Translation-en     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free amd64 Packages                  
Get:33 [http://repository.glx-dock.org](http://repository.glx-dock.org) oneiric/cairo-dock i386 Packages [5,186 B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free amd64 Packages              
Ign [http://repository.glx-dock.org](http://repository.glx-dock.org) oneiric/cairo-dock TranslationIndex         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex            
Ign [http://repository.glx-dock.org](http://repository.glx-dock.org) oneiric/cairo-dock Translation-en_US        
Ign [http://repository.glx-dock.org](http://repository.glx-dock.org) oneiric/cairo-dock Translation-en           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en
Fetched 1,089 kB in 27s (39.4 kB/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
khalid@khalid-H55M-USB3:~$

---

### Post by garvinrick4 on 2011-10-19
See all of these go into Software sources and uncheck these so as to make them out of play.
They must have no oneiric ppa available.
404  Not Found
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") oneiric/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") oneiric/main i386 Packages                        
W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/...source/Sources]("http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/source/Sources")  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/...amd64/Packages]("http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages")  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/...-i386/Packages]("http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-i386/Packages")  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...source/Sources]("http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources")  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...amd64/Packages]("http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages")  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...-i386/Packages]("http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages")  404  Not Found
Click on this screenshot will show you were you can uncheck them.
They are also in this path
gedit /etc/apt/sources.list.d

---

### Post by nobody850 on 2011-10-19
i maneged to find 4 of the 6 you told me to unchecked: 2 from the xbmc and 2 from the am-monkeyd

i went to the path but it was not correct.

---

### Post by garvinrick4 on 2011-10-19
> **nobody850 said:**
> i maneged to find 4 of the 6 you told me to unchecked: 2 from the xbmc and 2 from the am-monkeyd

i went to the path but it was not correct. Get the launchpad.net oneiric's also.
sorry no gedit just follow path in file system to see them. /etc/apt/sources.list.d

---

### Post by nobody850 on 2011-10-19
o man, i still don't understand. 
i i went to the file system and tried to delete them but cud not do it.

sorry for this taking to long of your time.

---

### Post by nobody850 on 2011-10-19
ok so unlicked every thing that had launchpad in it, now it updates no problem.
any more tips?

---

### Post by tibasic on 2011-10-31
As I recall the older versions of Ubuntu used Synaptic for updating. It's not a pretty way, but I got around this by installing Synaptic Package Manager and clicking "Mark all Upgrades" then clicking apply. Hit ok a few more times and you're on your way.

---

### Post by subehsharma on 2011-11-10
Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

---

### Post by kneeki on 2012-03-07
> **garvinrick4 said:**
> Key for medibuntu repositorys.

```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
``````
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```Chromium-browser do you have a .ppa for chromium-browser=need the key:
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)
Or google Launchpad.net ppa for chromium and install key if that is where you got your ppa from.
Here it is:   [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)
following this up with an ```
sudo apt-get update
``` fixed the problem for me. Thanks!

---

