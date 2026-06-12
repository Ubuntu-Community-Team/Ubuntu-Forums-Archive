---
title: "Update not working"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by joeccash on 2011-07-25
I'm living in Ireland and for the last 60 days, I haven't been able to update ubuntu. Using the main server whenever I tried to update with the update manager, it said 'No updates to install'. If I click 'Check', it says 'Updating Cache' and then nothing happens.

When I use 'sudo apt-get update', I get the following:

0% [Connecting to 10.51.255.250 (10.51.255.250)] [Connecting to 10.51.255.250 (^0% [Connecting to 10.51.255.250 (10.51.255.250)] [Connecting to 10.51.255.250 (^Err [http://mirror.krystal.co.uk](http://mirror.krystal.co.uk) natty InRelease                                
  
Err [http://mirror.krystal.co.uk](http://mirror.krystal.co.uk) natty-updates InRelease                        
  
Err [http://mirror.krystal.co.uk](http://mirror.krystal.co.uk) natty-security InRelease                       
  
Err [http://mirror.krystal.co.uk](http://mirror.krystal.co.uk) natty Release.gpg                              
  Unable to connect to 10.51.255.250:8080:
Err [http://mirror.krystal.co.uk](http://mirror.krystal.co.uk) natty-updates Release.gpg                      
  Unable to connect to 10.51.255.250:8080:
Err [http://mirror.krystal.co.uk](http://mirror.krystal.co.uk) natty-security Release.gpg                     
  Unable to connect to 10.51.255.250:8080:
Err [http://dl.google.com](http://dl.google.com) stable InRelease                                      
  
Err [http://dl.google.com](http://dl.google.com) stable InRelease                                      
  
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
  Unable to connect to 10.51.255.250:8080:
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
  Unable to connect to 10.51.255.250:8080:
Err [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
  
Err [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
  Unable to connect to 10.51.255.250:8080:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease    
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg  
  Unable to connect to 10.51.255.250:8080:
Reading package lists... Done
W: Failed to fetch [http://mirror.krystal.co.uk/ubuntu/dists/natty/InRelease](http://mirror.krystal.co.uk/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://mirror.krystal.co.uk/ubuntu/dists/natty-updates/InRelease](http://mirror.krystal.co.uk/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://mirror.krystal.co.uk/ubuntu/dists/natty-security/InRelease](http://mirror.krystal.co.uk/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/dists/natty/InRelease](http://archive.canonical.com/dists/natty/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease](http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease)  

W: Failed to fetch [http://mirror.krystal.co.uk/ubuntu/dists/natty/Release.gpg](http://mirror.krystal.co.uk/ubuntu/dists/natty/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://mirror.krystal.co.uk/ubuntu/dists/natty-updates/Release.gpg](http://mirror.krystal.co.uk/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://mirror.krystal.co.uk/ubuntu/dists/natty-security/Release.gpg](http://mirror.krystal.co.uk/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://archive.canonical.com/dists/natty/Release.gpg](http://archive.canonical.com/dists/natty/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Some index files failed to download. They have been ignored, or old ones used instead.
joeccash@Supercom:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                                                                                                                             
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                                                                                                                                     
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease                                                                                      
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                                                                             
  Unable to connect to 10.51.255.250:8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg                                                                                     
  Unable to connect to 10.51.255.250:8080:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release.gpg                                                                                    
  Unable to connect to 10.51.255.250:8080:
Err [http://dl.google.com](http://dl.google.com) stable InRelease                                                                                                   
  
Err [http://dl.google.com](http://dl.google.com) stable InRelease                                                                                                   
  
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                 
  Unable to connect to 10.51.255.250:8080:
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                   
  Unable to connect to 10.51.255.250:8080:
Err [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                                              
  
Err [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                                            
  Unable to connect to 10.51.255.250:8080:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease    
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg  
  Unable to connect to 10.51.255.250:8080:
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/dists/natty/InRelease](http://archive.canonical.com/dists/natty/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease](http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://archive.canonical.com/dists/natty/Release.gpg](http://archive.canonical.com/dists/natty/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Some index files failed to download. They have been ignored, or old ones used instead.


If I change the server to the best server, I get this message right after changing:
W: Failed to fetch [http://ftp.heanet.ie/pub/ubuntu/dists/natty/InRelease](http://ftp.heanet.ie/pub/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ftp.heanet.ie/pub/ubuntu/dists/natty-updates/InRelease](http://ftp.heanet.ie/pub/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ftp.heanet.ie/pub/ubuntu/dists/natty-security/InRelease](http://ftp.heanet.ie/pub/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/dists/natty/InRelease](http://archive.canonical.com/dists/natty/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease](http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://archive.canonical.com/dists/natty/Release.gpg](http://archive.canonical.com/dists/natty/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://ftp.heanet.ie/pub/ubuntu/dists/natty/Release.gpg](http://ftp.heanet.ie/pub/ubuntu/dists/natty/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://ftp.heanet.ie/pub/ubuntu/dists/natty-updates/Release.gpg](http://ftp.heanet.ie/pub/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Failed to fetch [http://ftp.heanet.ie/pub/ubuntu/dists/natty-security/Release.gpg](http://ftp.heanet.ie/pub/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to 10.51.255.250:8080:

W: Some index files failed to download. They have been ignored, or old ones used instead.


The same thing happens when I try to update and I get the same message when I change the server back to the main server.

---

### Post by raja.genupula on 2011-07-25
try this 
               ```
sudo rm -rf /var/lib/apt/lists/*
```
```
sudo apt-get update
```

---

### Post by joeccash on 2011-07-25
> **raja.genupula said:**
> try this 
               ```
sudo rm -rf /var/lib/apt/lists/*
```
```
sudo apt-get update
```

No good, same result as before.

---

### Post by raja.genupula on 2011-07-25
i am not sure about this because i am out of my pc but try this man 
go to update manager settings and at sources change your server to main and check again

---

### Post by richgj700 on 2011-10-13
You beauty! Been having all sorts of problems updating for a while, I checked my sources in settings on the update manager and it was set to United Kingdom servers, switched to Main and reloaded, updates have been working great since. Just in time to upgrade to  11.10 ;) Thanks Raja

---

