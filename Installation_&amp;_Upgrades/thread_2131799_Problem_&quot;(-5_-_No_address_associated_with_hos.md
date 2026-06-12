---
title: "Problem &quot;(-5 - No address associated with hostname)&quot;"
date: 2013-04-02
forum: Installation &amp; Upgrades
---

### Post by WaNaBePi on 2013-04-02
How do I fix these errors and warnings at the end?

```
default@default-laptop:~$ sudo apt-get update
[sudo] password for default: 
Get:1 http://archive.canonical.com precise Release.gpg [198 B]
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://archive.canonical.com precise Release                               
Hit http://archive.canonical.com precise Release                               
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://us.archive.ubuntu.com precise Release                               
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://us.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com lucid-backports/main amd64 Packages           
Hit http://us.archive.ubuntu.com lucid-backports/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com lucid-backports/universe amd64 Packages       
Hit http://us.archive.ubuntu.com lucid-backports/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com lucid-backports/main i386 Packages            
Hit http://us.archive.ubuntu.com lucid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com lucid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com lucid-backports/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com lucid-backports/main TranslationIndex         
Ign http://us.archive.ubuntu.com lucid-backports/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com lucid-backports/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com lucid-backports/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:4 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [191 kB]
Get:5 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [592 kB]
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Get:6 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,418 B]
Get:7 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]
Get:8 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [194 kB]
Get:9 http://us.archive.ubuntu.com precise-updates/main i386 Packages [603 kB] 
Get:10 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Get:11 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.1 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en           
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en     
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en     
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en       
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Err http://packages.medibuntu.org precise Release.gpg                          
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Hit http://packages.medibuntu.org precise Release                              
Ign http://packages.medibuntu.org precise/free amd64 Packages/DiffIndex        
Ign http://packages.medibuntu.org precise/non-free amd64 Packages/DiffIndex
Ign http://packages.medibuntu.org precise/free i386 Packages/DiffIndex    
Ign http://packages.medibuntu.org precise/non-free i386 Packages/DiffIndex     
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Hit http://packages.medibuntu.org precise/free amd64 Packages                  
Hit http://packages.medibuntu.org precise/non-free amd64 Packages              
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Err http://ppa.launchpad.net precise Release.gpg                               
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Err http://security.ubuntu.com precise-security Release.gpg                    
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Get:12 http://security.ubuntu.com precise-security Release [49.6 kB]           
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://security.ubuntu.com precise-security/universe amd64 Packages/DiffIndex
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://security.ubuntu.com precise-security/main amd64 Packages/DiffIndex  
Ign http://security.ubuntu.com precise-security/multiverse amd64 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/restricted amd64 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/universe i386 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/main i386 Packages/DiffIndex   
Ign http://security.ubuntu.com precise-security/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/restricted i386 Packages/DiffIndex
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Get:13 http://security.ubuntu.com precise-security/universe amd64 Packages [71.0 kB]
Ign http://packages.medibuntu.org precise/non-free Translation-en_US
Get:14 http://security.ubuntu.com precise-security/main amd64 Packages [233 kB]
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Get:15 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,186 B]
Get:16 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:17 http://security.ubuntu.com precise-security/universe i386 Packages [72.9 kB]
Get:18 http://security.ubuntu.com precise-security/main i386 Packages [243 kB]
Get:19 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Get:20 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 2,351 kB in 22s (103 kB/s)                
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/precise/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/n-muench/vlc/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
default@default-laptop:~$
```

---

### Post by sanderj on 2013-04-03
Which Ubuntu version?

Looks like [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/574886) , so I would try work-around mentioned there: put 

```
nameserver 8.8.8.8 
```

in /etc/resolv.conf

---

### Post by WaNaBePi on 2013-04-04
humm creepy, google owns the world. Thats it huh?

> # Generated by NetworkManager
domain Belkin
search Belkin
nameserver 127.0.0.1
nameserver 8.8.8.8

Looks like this now saved it and all.

now i get

```
default@default-laptop:~$ sudo apt-get update
[sudo] password for default: 
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise-updates Release                       
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://security.ubuntu.com precise-security Release                        
Hit http://archive.canonical.com precise Release                               
Hit http://us.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com lucid-backports/main amd64 Packages           
Hit http://us.archive.ubuntu.com lucid-backports/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com lucid-backports/universe amd64 Packages       
Hit http://us.archive.ubuntu.com lucid-backports/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com lucid-backports/main i386 Packages            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com lucid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com lucid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com lucid-backports/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com lucid-backports/main TranslationIndex         
Ign http://us.archive.ubuntu.com lucid-backports/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com lucid-backports/restricted TranslationIndex   
Hit http://security.ubuntu.com precise-security/universe amd64 Packages        
Hit http://archive.canonical.com precise Release                               
Ign http://us.archive.ubuntu.com lucid-backports/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://security.ubuntu.com precise-security/main amd64 Packages            
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages      
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://packages.medibuntu.org precise Release.gpg                          
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages       
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages           
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://packages.medibuntu.org precise Release                              
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://packages.medibuntu.org precise/free amd64 Packages                  
Hit http://packages.medibuntu.org precise/non-free amd64 Packages              
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en           
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en     
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en     
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en       
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://packages.medibuntu.org precise/free TranslationIndex      
Ign http://archive.canonical.com precise/partner Translation-en      
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://packages.medibuntu.org precise/non-free TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://packages.medibuntu.org precise/free Translation-en_US
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://packages.medibuntu.org precise/non-free Translation-en_US
Ign http://packages.medibuntu.org precise/non-free Translation-en
Reading package lists... Done                             
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
default@default-laptop:~$ 

```

That's different at least. I assume it's fixed because there would be the old warnings and the new ones together if it wasn't fixed, right?

So how do I fix this new "W:"?

Thanks for your help, sincerely.

---

### Post by sanderj on 2013-04-05
"Duplicate sources.list entry " ... so check /etc/apt/sources.list for double entries ... ?

---

### Post by WaNaBePi on 2013-04-06
Thank you

 Ran ```
gksu nautilus
``` Then navigated to that location, deleted matching lines, saved and then ran:
```
default@default-laptop:~$ sudo apt-get update
[sudo] password for default: 
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://us.archive.ubuntu.com precise Release                               
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://packages.medibuntu.org precise Release.gpg                          
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://extras.ubuntu.com precise Release                                   
Hit http://security.ubuntu.com precise-security Release                        
Hit http://archive.canonical.com precise Release                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://packages.medibuntu.org precise Release                              
Hit http://archive.canonical.com precise Release                               
Hit http://security.ubuntu.com precise-security/universe amd64 Packages        
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com lucid-backports/main amd64 Packages           
Hit http://us.archive.ubuntu.com lucid-backports/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com lucid-backports/universe amd64 Packages       
Hit http://us.archive.ubuntu.com lucid-backports/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com lucid-backports/main i386 Packages            
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com lucid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com lucid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com lucid-backports/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com lucid-backports/main TranslationIndex         
Ign http://us.archive.ubuntu.com lucid-backports/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com lucid-backports/restricted TranslationIndex   
Hit http://security.ubuntu.com precise-security/main amd64 Packages            
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages      
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://us.archive.ubuntu.com lucid-backports/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://packages.medibuntu.org precise/free amd64 Packages                  
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:4 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [191 kB]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://packages.medibuntu.org precise/non-free amd64 Packages              
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:5 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [593 kB]
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Get:6 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,418 B]
Get:7 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Get:8 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [194 kB]
Get:9 http://us.archive.ubuntu.com precise-updates/main i386 Packages [603 kB] 
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Ign http://archive.canonical.com precise/partner Translation-en_US             
Get:10 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Get:11 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.1 kB]
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en       
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-en_US           
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Fetched 1,671 kB in 9s (174 kB/s)                                              
Reading package lists... Done
default@default-laptop:~$ 

```

No W: at all. Again thank you very much. SOLVED

---

