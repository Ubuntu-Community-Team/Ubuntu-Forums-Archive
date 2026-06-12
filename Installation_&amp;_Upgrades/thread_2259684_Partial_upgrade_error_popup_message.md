---
title: "Partial upgrade error popup message"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by Philip Gray on 2015-01-06
Good evening

I am using Ubuntu 12.04LTS 64 bit version with the GNOME 2 fallback desktop. Since last week after I did an update I am now receiving an odd popup when I open my Update Manager. It advises me that 'Not all updates can be installed' and it has a 'Partial Upgrade' button. Also the 'Upgrade to 14.04.1LTS' button has disappeared. I also have a package in Update Manager that is being displayed that I cannot select. Update Manager advises me that there are no packages to install.

I ran sudo apt-get clean and then sudo apt-get update in the terminal and received the response below. I tried changing the'Show me updates' to Never and then refreshed the Software Sources to see if the popup would go away and if it was related to the 14.04.01 upgrade button. It did not make any difference. Does anyone have an idea what is going on here?

Regards
Philip


```
philip@philip-blikkie:~$ sudo apt-get clean
[sudo] password for philip: 
philip@philip-blikkie:~$ sudo apt-get update
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [596 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [596 B]          
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [596 B]                         
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
  
Get:4 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg [596 B]                     
Get:5 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [596 B]                          
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [596 B]              
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
  
Get:7 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release.gpg [596 B]                 
Get:8 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release [596 B]                         
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                   
  
Get:9 [http://deb.opera.com](http://deb.opera.com) stable Release [596 B]                              
Get:10 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release.gpg [596 B] 
Err [http://deb.opera.com](http://deb.opera.com) stable Release                                        
  
Get:11 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports Release.gpg [596 B]
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]
Get:13 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release [596 B]
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release                               
  
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]                    
Get:15 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release [596 B]
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release                       
  
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]                    
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]
Get:18 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports Release [596 B]
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports Release 
  
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
  
Fetched 16,7 kB in 0s (46,5 kB/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/precise/Release](http://linux.dropbox.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/precise/Release](http://za.archive.ubuntu.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://za.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://za.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  

W: Failed to fetch [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/precise/Release](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/precise/Release](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/gambas-team/gambas3/ubuntu/dists/precise/Release](http://ppa.launchpad.net/gambas-team/gambas3/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/noobslab/screenlets/ubuntu/dists/precise/Release](http://ppa.launchpad.net/noobslab/screenlets/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/Release](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/precise/Release](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/precise/Release](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
philip@philip-blikkie:~$ clear

philip@philip-blikkie:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [596 B]
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [596 B]                                                                         
Get:3 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg [596 B]                                                                         
Get:4 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [596 B]                                                                              
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [596 B]                                                                  
Get:6 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release.gpg [596 B]                                                                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                                                            
  
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [596 B]                                                                             
Get:8 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release [596 B]                                                              
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                           
  
Err [http://linux.dropbox.com](http://linux.dropbox.com) precise Release                                                 
  
Get:9 [http://deb.opera.com](http://deb.opera.com) stable Release [596 B]                                            
Err [http://deb.opera.com](http://deb.opera.com) stable Release                                 
  
Get:10 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release.gpg [596 B]
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]
Get:12 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports Release.gpg [596 B]
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]
Get:15 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release [596 B]
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release                                                      
  
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]                                           
Get:17 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release [596 B]
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release                                              
  
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]                                           
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]
Get:20 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports Release [596 B]
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports Release    
  
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [596 B]
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                
  
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [596 B]                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
  
Fetched 16,7 kB in 0s (46,9 kB/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/precise/Release](http://linux.dropbox.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/precise/Release](http://za.archive.ubuntu.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://za.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  

W: Failed to fetch [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/precise/Release](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://za.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  

W: Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/precise/Release](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/gambas-team/gambas3/ubuntu/dists/precise/Release](http://ppa.launchpad.net/gambas-team/gambas3/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/noobslab/screenlets/ubuntu/dists/precise/Release](http://ppa.launchpad.net/noobslab/screenlets/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/Release](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/precise/Release](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/precise/Release](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
philip@philip-blikkie:~$
```

---

### Post by slickymaster on 2015-01-06
Try this at a terminal window:
```
sudo apt-get clean
sudo mv /var/lib/apt/lists /tmp
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
```

---

### Post by Philip Gray on 2015-01-09
> **slickymaster said:**
> Try this at a terminal window:
```
sudo apt-get clean
sudo mv /var/lib/apt/lists /tmp
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
```

Hi slickymaster

Thank you this got ris of the popup. I still had the disabled item. I went into Synaptic and saw that xmbc had an upgrade star next to it. I ran the upgrade and Synaptic installed Kodi and removed the xbmc packages. When I re-ran Update Manager the disabled item was gone.

Regards
Philip

---

