---
title: "sudo apt-get &quot;Failed to fetch&quot; dropbox error"
date: 2014-03-18
forum: Installation &amp; Upgrades
---

### Post by Jonathan_Vo on 2014-03-18
Typing in the command sudo apt-get update causes the following errors at the bottom where it says "Failed to fetch...". I also noticed that I am unable to start Dropbox now. I'm relatively inexperienced in using Linux, so detailed instructions/explanations on how to fix this would be much appreciated.

```
sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Ign [http://linux.dropbox.com](http://linux.dropbox.com) release Release.gpg                               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:4 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg [489 B]                     
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Ign [http://linux.dropbox.com](http://linux.dropbox.com) release Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [100 kB]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Get:7 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release [2,603 B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Ign [http://linux.dropbox.com](http://linux.dropbox.com) release/-sc) TranslationIndex                     
Ign [http://linux.dropbox.com](http://linux.dropbox.com) release/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [453 kB]       
Get:9 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Sources [426 B]                    
Get:10 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main amd64 Packages [1,142 B]          
Get:11 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages [1,142 B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,789 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [373 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Err [http://linux.dropbox.com](http://linux.dropbox.com) release/-sc) Sources                              
  404  Not Found
Err [http://linux.dropbox.com](http://linux.dropbox.com) release/main Sources                              
  404  Not Found
Err [http://linux.dropbox.com](http://linux.dropbox.com) release/-sc) amd64 Packages                       
  404  Not Found
Err [http://linux.dropbox.com](http://linux.dropbox.com) release/main amd64 Packages                       
  404  Not Found
Err [http://linux.dropbox.com](http://linux.dropbox.com) release/-sc) i386 Packages                        
  404  Not Found
Err [http://linux.dropbox.com](http://linux.dropbox.com) release/main i386 Packages                        
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [91.3 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://linux.dropbox.com](http://linux.dropbox.com) release/-sc) Translation-en_US                    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) release/-sc) Translation-en                       
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,446 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [399 kB] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,028 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [105 kB]  
Ign [http://linux.dropbox.com](http://linux.dropbox.com) release/main Translation-en_US                    
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,900 B]
Ign [http://linux.dropbox.com](http://linux.dropbox.com) release/main Translation-en                       
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en_US                    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                       
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [759 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [96.1 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,646 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [12.2 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [237 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [15.3 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [783 kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [12.2 kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [242 kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [15.5 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 3,865 kB in 15s (243 kB/s)                                             
W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/release/-sc)/source/Sources](http://linux.dropbox.com/ubuntu/dists/release/-sc)/source/Sources)  404  Not Found

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/release/main/source/Sources](http://linux.dropbox.com/ubuntu/dists/release/main/source/Sources)  404  Not Found

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/release/-sc)/binary-amd64/Packages](http://linux.dropbox.com/ubuntu/dists/release/-sc)/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/release/main/binary-amd64/Packages](http://linux.dropbox.com/ubuntu/dists/release/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/release/-sc)/binary-i386/Packages](http://linux.dropbox.com/ubuntu/dists/release/-sc)/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/release/main/binary-i386/Packages](http://linux.dropbox.com/ubuntu/dists/release/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by buzzingrobot on 2014-03-18
> **Jonathan_Vo said:**
> 
```
[p://ppa.launchpad.net]("http://ppa.launchpad.net") precise/main TranslationIndex                     
Err [http://linux.dropbox.com](http://linux.dropbox.com) release/-sc) Sources                              
  404  Not Found

....

```

"404" is the code used on the web to indicate no response was received from a server. Typically, this means the server is temporarily offline, either for maintenance or due to a malfunction.

Wait a while and try again. (If Dropbox goes offline for any significant amount of time, you'll see complaints all over the web.)

[Your system maintains a database of all the software installed on it.  "Update" queries the servers that are the repositories for that software to determine if updates are available. In this case, Dropbox didn't respond, and the "fetch" message is update's way of telling you that.]

---

### Post by Jonathan_Vo on 2014-03-18
I'm not sure if nine hours is an ample enough time to wait, but I'm still getting the same error.

---

### Post by buzzingrobot on 2014-03-19
I've installed Dropbox using the Ubuntu package at the Dropbox site. No 404's on updating. The URL the updater uses is contained in "/etc/apt/sources.list.d/dropbox.list". Here's the line:```

deb http://linux.dropbox.com/ubuntu precise main

```

The URL's quoted in your post also return 404's here.

---

### Post by Jonathan_Vo on 2014-03-27
Thanks for the help guys. I tried using your command buzzing, but it said "no command deb could be found." Also, is there a way to get rid of the fetch error messages?

---

### Post by Ubi_one_2014 on 2014-03-27
> **Jonathan_Vo said:**
> Thanks for the help guys. I tried using your command buzzing, but it said "no command deb could be found." Also, is there a way to get rid of the fetch error messages?

1- open a terminal
2- cd /etc/apt
3- sudo kate sources.list
    a password need to be entered, that&#347; your password of the user

paste below line in the bottom of the list

deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) precise main


- save

sudo su - [enter ]
apt-get update [enter]
apt-get install dropbox [enter]
after everything has been finished, type   exit [enter]

---

### Post by buzzingrobot on 2014-03-27
Sorry, as Ubu_One explained, it's a line in the sources.list file, not a command to be executed.

When you use Software Center, Synaptic, apt-get, etc., to retrieve and install packages, the packages come from repositories listed in /etc/apt/sources.list.  When you refresh Software Center or Synaptic, or do an "apt-get update", you are updating a local database of all the available packages currently available in those repositories.  If newer versions of already-installed packages are found, those will be installed with an "apt-get upgrade" or the equivalent in one of the GUI tools. Your original '404' problem with the Dropbox repository happened because that server did not respond to the query sent to it from your machine.

---

### Post by Jonathan_Vo on 2014-03-27
I followed what you said. I still get an error message.

```
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://us.archive.ubuntu.com precise-updates Release                       
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]                     
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Get:2 http://linux.dropbox.com precise Release [2,603 B]                       
Err http://linux.dropbox.com precise Release                                   
  
Get:3 http://repository.spotify.com stable Release.gpg [489 B]                 
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://us.archive.ubuntu.com precise-updates/main Sources                  
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://us.archive.ubuntu.com precise-updates/universe Sources              
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages           
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages       
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://repository.spotify.com stable Release                               
Ign http://repository.spotify.com stable Release                               
Hit http://security.ubuntu.com precise-security Release                        
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Ign http://repository.spotify.com stable/non-free amd64 Packages/DiffIndex
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en         
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Ign http://repository.spotify.com stable/non-free i386 Packages/DiffIndex      
Ign http://repository.spotify.com stable/non-free TranslationIndex             
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://security.ubuntu.com precise-security/restricted Sources   
Hit http://security.ubuntu.com precise-security/universe Sources     
Hit http://security.ubuntu.com precise-security/multiverse Sources   
Hit http://security.ubuntu.com precise-security/main amd64 Packages  
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://ppa.launchpad.net precise Release                         
Hit http://security.ubuntu.com precise-security/main i386 Packages   
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources                    
Hit http://ppa.launchpad.net precise/main amd64 Packages             
Hit http://ppa.launchpad.net precise/main i386 Packages              
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://ppa.launchpad.net precise/main i386 Packages              
Ign http://ppa.launchpad.net precise/main TranslationIndex           
Hit http://ppa.launchpad.net precise/main Sources                    
Hit http://ppa.launchpad.net precise/main amd64 Packages             
Hit http://ppa.launchpad.net precise/main i386 Packages              
Ign http://ppa.launchpad.net precise/main TranslationIndex           
Hit http://ppa.launchpad.net precise/main Sources                    
Hit http://ppa.launchpad.net precise/main amd64 Packages             
Hit http://ppa.launchpad.net precise/main i386 Packages              
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Ign http://ppa.launchpad.net precise/main TranslationIndex           
Hit http://ppa.launchpad.net precise/main Sources                    
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://repository.spotify.com stable/non-free amd64 Packages     
Hit http://repository.spotify.com stable/non-free i386 Packages
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://repository.spotify.com stable/non-free Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://repository.spotify.com stable/non-free Translation-en
Fetched 979 B in 1s (558 B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://linux.dropbox.com precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912E

W: GPG error: http://repository.spotify.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/precise/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  Unable to find expected entry 'partner/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by Ubi_one_2014 on 2014-03-28
remove the line from your sources.list

go to [https://www.dropbox.com/install?os=lnx](https://www.dropbox.com/install?os=lnx)

download your package, 32bits or 64 bits

open a terminal
open dolphin, or an other file manager
open the download folder
double click on the dropbox file ( dropbox_1.6.0-XXX)
follow instructions

---

### Post by buzzingrobot on 2014-03-28
I suspect the OP has the Dropbox package installed, since he mentioned that it isn't working.  I'm a bit confused, though.  Was Dropbox installed from the repos, from the Dropbox site, or another way? In the first post, the Dropbox repo returned a 404.  In the later post, no 404 is shown, and the complaint about Dropbox, and Spotify, is a missing/bad key.

Also, just in case,  Dropbox doesn't run until the the Dropbox binary is downloaded and installed, and it is not included in the Dropbox debs.  If the OP did not see this explicitly happen, he should click the Dropbox icon. I.e., the Dropbox package that is initially installed, when executed, installs another program that will download and install the actual proprietrary Dropbox code. I've seen instances when that second program is not automatically executed.

---

### Post by Jonathan_Vo on 2014-03-31
Thanks for your help guys. My dropbox installation went smoothly, and I can now run it. However, when I run the sudo apt-get command, I still get the same error as in my previous post, with the "Failed to fetch" line at the bottom.

---

