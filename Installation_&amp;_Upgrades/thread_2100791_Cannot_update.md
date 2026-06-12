---
title: "Cannot update"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by jcpahman77 on 2013-01-02
I get the following error when I try to check for updates, I also have a red triangle with an exclamation point at the top right of my screen by the network and sound icons. I'm posting from the computer in question, so I know my internet connection is fine, I don't know what causes and how to fix the below error. Help?


W:Failed to fetch [http://archive.cononical.com/dists/precise/Release.gpg](http://archive.cononical.com/dists/precise/Release.gpg)  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.cononical.com/dists/precise/partner/source/Sources](http://archive.cononical.com/dists/precise/partner/source/Sources)  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.cononical.com/dists/precise/partner/binary-amd64/Packages](http://archive.cononical.com/dists/precise/partner/binary-amd64/Packages)  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.cononical.com/dists/precise/partner/binary-i386/Packages](http://archive.cononical.com/dists/precise/partner/binary-i386/Packages)  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.cononical.com/dists/precise/partner/i18n/Translation-en](http://archive.cononical.com/dists/precise/partner/i18n/Translation-en)  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ibjsb4 on 2013-01-02
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And please post the output.

---

### Post by jcpahman77 on 2013-01-02
> **ibjsb4 said:**
> [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And please post the output.

Ign [http://archive.cononical.com](http://archive.cononical.com) precise InRelease
Err [http://archive.cononical.com](http://archive.cononical.com) precise Release.gpg                           
  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.cononical.com](http://archive.cononical.com) precise Release                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://archive.cononical.com](http://archive.cononical.com) precise/partner TranslationIndex              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [198 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [13.0 kB]                  
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [4,419 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [67.5 kB]  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,244 B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [448 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [8,167 B]          
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [8,167 B]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [8,366 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [163 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,671 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [457 kB]
Err [http://archive.cononical.com](http://archive.cononical.com) precise/partner Sources                       
  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)
Err [http://archive.cononical.com](http://archive.cononical.com) precise/partner amd64 Packages                
  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)
Err [http://archive.cononical.com](http://archive.cononical.com) precise/partner i386 Packages                 
  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)
Err [http://archive.cononical.com](http://archive.cononical.com) precise/partner Translation-en_US             
  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)
Err [http://archive.cononical.com](http://archive.cononical.com) precise/partner Translation-en
  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [8,374 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [165 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,675 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Fetched 1,633 kB in 7s (220 kB/s)                                              
W: Failed to fetch [http://archive.cononical.com/dists/precise/Release.gpg](http://archive.cononical.com/dists/precise/Release.gpg)  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.cononical.com/dists/precise/partner/source/Sources](http://archive.cononical.com/dists/precise/partner/source/Sources)  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.cononical.com/dists/precise/partner/binary-amd64/Packages](http://archive.cononical.com/dists/precise/partner/binary-amd64/Packages)  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.cononical.com/dists/precise/partner/binary-i386/Packages](http://archive.cononical.com/dists/precise/partner/binary-i386/Packages)  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.cononical.com/dists/precise/partner/i18n/Translation-en_US](http://archive.cononical.com/dists/precise/partner/i18n/Translation-en_US)  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.cononical.com/dists/precise/partner/i18n/Translation-en](http://archive.cononical.com/dists/precise/partner/i18n/Translation-en)  Something wicked happened resolving 'archive.cononical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ibjsb4 on 2013-01-02
Weird.  All those have c**o**nonical spelled wrong, should be c**a**nonical.

Do you know how to edit your sources list?  In terminal:

```
gksudo gedit /etc/apt/sources.list
```

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Post back if not sure about this  :)

---

### Post by jcpahman77 on 2013-01-02
> **ibjsb4 said:**
> Weird.  All those have c**o**nonical spelled wrong, should be c**a**nonical.

Do you know how to edit your sources list?  In terminal:

```
gksudo gedit /etc/apt/sources.list
```

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Post back if not sure about this  :)

That did it. It appears that repository was one I added when working on installing Skype. I very likely made a typo. I don't usually copy/paste the code from websites, I like to type it myself; brings me back to my DOS days.

---

### Post by ibjsb4 on 2013-01-02
Ok, not so weird  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums

---

### Post by jcpahman77 on 2013-01-02
> **ibjsb4 said:**
> Ok, not so weird  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums

Thanks, I actually posted a bit a couple months ago when I first installed 12.04 LTS on this computer. I had some issues (that all turned out to be improper BIOS settings) and the board was very helpful.

My latest venture in Linux is trying to learn how to use the MS Kinnect as a webcam for Skype. I can connect to the camera and I get a good signal, and Skype starts and runs fine, but it doesn't get a signal from the webcam. I feel like I'm missing something simple.

---

### Post by ibjsb4 on 2013-01-02
No webcam here, but should be able to find some help by starting another thread on it.

I can point you here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Skype+&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Skype+&as_qdr=all&sa=Google+Search&lang=en)

Good luck

---

