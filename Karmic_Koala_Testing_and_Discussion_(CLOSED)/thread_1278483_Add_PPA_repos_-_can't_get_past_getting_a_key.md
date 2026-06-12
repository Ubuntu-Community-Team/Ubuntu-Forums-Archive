---
title: "Add PPA repos - can't get past getting a key?"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by virtualu2 on 2009-09-29
Hi,
I am trying to add a couple repos I would think are safe....

I have tried to run the command to get the repo key on 3 so far and it fails everytime, just hangs in the terminal.

The ones I have tried are:
[http://www.bisigi-project.org/?page_id=8&lang=en](http://www.bisigi-project.org/?page_id=8&lang=en)
[FONT=tahoma][COLOR=#000000]gpg[/COLOR][COLOR=#000000] --keyserver hkp://keyserver.ubuntu.com:11371 --recv-key 881574DE && gpg -a --export 881574DE | sudo apt-key add -

[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

And then the mozilla repo as well fails...



[/COLOR][/FONT]

---

### Post by DougieFresh4U on 2009-09-29
One way to obtain the key is from the page where you got the repo. I just save it and the under System>Administration>Software Sources  you can add it there manually.

---

### Post by ninjapirate89 on 2009-09-29
If I understand correctly you have added PPA repos but can't get the keys to work. If this is correct, try this link. It has a script you can download that will automatically add GPG keys for you.

[http://d0od.blogspot.com/2009/09/automatically-install-missing-ppa-gpg.html]("http://d0od.blogspot.com/2009/09/automatically-install-missing-ppa-gpg.html")

---

### Post by DougieFresh4U on 2009-09-29
> **ninjapirate89 said:**
> 

[http://d0od.blogspot.com/2009/09/automatically-install-missing-ppa-gpg.html]("http://d0od.blogspot.com/2009/09/automatically-install-missing-ppa-gpg.html")

Thanks, I like that

---

### Post by ninjapirate89 on 2009-09-29
> **DougieFresh4U said:**
> Thanks, I like that

No problem. That is a very nice blog for discovering new things about ubuntu.

---

### Post by Starks on 2009-09-29
According to people on IRC, the keyserver is down.

---

### Post by drs305 on 2009-09-29
The server has been a bit erratic lately.

One thing that hasn't been mentioned yet is the new feature in Karmic which allows you to run one command which automatically adds a Launchpad PPA repository (to /etc/apt/sources.list.d) *and* imports the key:
[U][I]
Corrected:[/I][/U]
```

add-apt-repository ppa:bisigi

```

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by Starks on 2009-09-29
drs305, launchpad has incorporated it into their PPA sites.

Example: [PPA for Ubuntu Mozilla Daily Build Team     ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")
> **Adding this PPA to your system**

                  You can update your system with unsupported packages from           this untrusted PPA by adding           **ppa:ubuntu-mozilla-daily/ppa**           to your system's Software Sources.           Not using Ubuntu 9.10 (karmic)?


---

### Post by virtualu2 on 2009-09-29
Thanks, so is it best just to run the command mentioned in the reply or just edit the sources file, or does it even matter?  I like the command line idea, but how do you figure out what the command is for any repo you want to add?  IE:  Mozilla?

---

### Post by bluenova on 2009-09-30
> **virtualu2 said:**
> Thanks, so is it best just to run the command mentioned in the reply or just edit the sources file, or does it even matter?  I like the command line idea, but how do you figure out what the command is for any repo you want to add?  IE:  Mozilla?

just add the source:
ppa:ubuntu-mozilla-daily/ppa 
to your sources list or
sudo apt-add-repository ppa:ubuntu-mozilla-daily

---

### Post by shakaran on 2009-09-30
$ sudo apt-add-repository ppa:ubuntu-mozilla-daily
sudo: apt-add-repository: command not found

---

### Post by drs305 on 2009-09-30
> **shakaran said:**
> $ sudo apt-add-repository ppa:ubuntu-mozilla-daily
sudo: apt-add-repository: command not found

Dyslexia strikes again:
```

sudo add-apt-repository ppa:ubuntu-mozilla-daily

```

---

### Post by shakaran on 2009-09-30
$ sudo add-apt-repository pidgin-developers/ppa
Error: 'pidgin-developers/ppa' invalid

"" You can update your system with unsupported packages from this untrusted PPA by adding ppa:pidgin-developers/ppa ""
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by Amaranth on 2009-09-30
You left off the ppa: part at the beginning.

---

### Post by shakaran on 2009-09-30
Thanks, but it dont work:

I get the key from ppa:
```
$ sudo add-apt-repository pidgin-developers
Error: 'pidgin-developers' invalid
shakaran@otorion:~/sandbox$ sudo add-apt-repository ppa:pidgin-developers/ppa
[sudo] password for shakaran: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 67265EB522BDD6B1C69E66ED7FB8BEE0A1F196A8
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: key A1F196A8: "Launchpad PPA for Pidgin Developers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```

And when I update the source, it say that the key for pidgin's ppa is invalid (The following signatures were invalid)

```
$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://ppa.launchpad.net jaunty Release.gpg                                                            
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                                                 
Hit http://packages.kirya.net sid Release.gpg                                                              
Hit http://ppa.launchpad.net jaunty Release.gpg                                                            
Ign http://dl.google.com stable/main Translation-en_US                                                     
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                                                 
Hit http://ppa.launchpad.net jaunty Release.gpg                                                            
Hit http://es.archive.ubuntu.com karmic-backports Release.gpg                                              
Ign http://packages.kirya.net sid/main Translation-en_US                                                   
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                                                 
Hit http://archive.ubuntu.com karmic Release.gpg                                                           
Ign http://es.archive.ubuntu.com karmic-backports/main Translation-en_US                                   
Get:2 http://ppa.launchpad.net karmic Release.gpg [307B]                                                   
Ign http://packages.kirya.net sid/contrib Translation-en_US                                                
Ign http://archive.ubuntu.com karmic/main Translation-en_US                                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                 
Hit http://ddebs.ubuntu.com karmic Release.gpg                                                             
Ign http://packages.kirya.net sid/non-free Translation-en_US                                               
Hit http://ppa.launchpad.net jaunty Release.gpg                                                            
Ign http://es.archive.ubuntu.com karmic-backports/restricted Translation-en_US                             
Ign http://ddebs.ubuntu.com karmic/main Translation-en_US                                                  
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                                                 
Hit http://packages.kirya.net sid Release                                                                  
Ign http://ddebs.ubuntu.com karmic/restricted Translation-en_US                                            
Hit http://ppa.launchpad.net jaunty Release.gpg                                                            
Get:3 http://dl.google.com stable Release [2,540B]                                                         
Hit http://packages.kirya.net sid/main Packages                                                            
Hit http://packages.kirya.net sid/contrib Packages                                                         
Ign http://ddebs.ubuntu.com karmic/universe Translation-en_US                                              
Hit http://packages.kirya.net sid/non-free Packages                                                        
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                                                 
Ign http://es.archive.ubuntu.com karmic-backports/universe Translation-en_US                               
Ign http://ddebs.ubuntu.com karmic/multiverse Translation-en_US                                            
Hit http://ddebs.ubuntu.com karmic Release                                                                 
Hit http://ppa.launchpad.net jaunty Release.gpg                                                            
Ign http://ddebs.ubuntu.com karmic/main Packages                                                           
Ign http://ddebs.ubuntu.com karmic/restricted Packages                                                     
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                                                 
Hit http://packages.kirya.net sid/main Sources                                                             
Ign http://ddebs.ubuntu.com karmic/universe Packages                                                       
Ign http://ddebs.ubuntu.com karmic/multiverse Packages                                                     
Ign http://ddebs.ubuntu.com karmic/main Packages                                                           
Ign http://ddebs.ubuntu.com karmic/restricted Packages                                                     
Hit http://packages.kirya.net sid/contrib Sources                                                          
Ign http://ddebs.ubuntu.com karmic/universe Packages                                                       
Ign http://ddebs.ubuntu.com karmic/multiverse Packages                                                     
Hit http://packages.kirya.net sid/non-free Sources                                                         
Ign http://es.archive.ubuntu.com karmic-backports/multiverse Translation-en_US                             
Hit http://es.archive.ubuntu.com karmic-backports Release                                                  
Get:4 http://download.virtualbox.org jaunty Release.gpg [197B]                                             
Hit http://es.archive.ubuntu.com karmic-backports/main Packages                                            
Get:5 http://dl.google.com stable/main Packages [654B]                                                     
Hit http://es.archive.ubuntu.com karmic-backports/restricted Packages                                      
Ign http://download.virtualbox.org jaunty/non-free Translation-en_US                                       
Get:6 http://download.virtualbox.org jaunty Release [3,454B]                                               
Ign http://download.virtualbox.org jaunty Release                                                          
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US                                          
Ign http://archive.ubuntu.com karmic/universe Translation-en_US                                            
Hit http://download.virtualbox.org jaunty/non-free Packages                                                
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US                                          
Hit http://es.archive.ubuntu.com karmic-backports/universe Packages                                        
Hit http://archive.ubuntu.com karmic-updates Release.gpg                                                   
Hit http://es.archive.ubuntu.com karmic-backports/multiverse Packages                                      
Hit http://es.archive.ubuntu.com karmic-backports/main Sources                                             
Ign http://archive.ubuntu.com karmic-updates/main Translation-en_US                                        
Hit http://ddebs.ubuntu.com karmic/main Packages                                                           
Hit http://es.archive.ubuntu.com karmic-backports/restricted Sources                                       
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-en_US                                  
Hit http://es.archive.ubuntu.com karmic-backports/universe Sources                                         
Ign http://archive.ubuntu.com karmic-updates/universe Translation-en_US                                    
Hit http://es.archive.ubuntu.com karmic-backports/multiverse Sources                                       
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-en_US                                  
Hit http://archive.ubuntu.com karmic-security Release.gpg                                                  
Ign http://archive.ubuntu.com karmic-security/main Translation-en_US                                       
Ign http://archive.ubuntu.com karmic-security/restricted Translation-en_US                                 
Ign http://archive.ubuntu.com karmic-security/universe Translation-en_US                                   
Hit http://ppa.launchpad.net jaunty Release.gpg                                                            
Hit http://ddebs.ubuntu.com karmic/restricted Packages                                                     
Ign http://archive.ubuntu.com karmic-security/multiverse Translation-en_US                       
Hit http://ddebs.ubuntu.com karmic/universe Packages                                                       
Get:7 http://archive.ubuntu.com karmic-backports Release.gpg [189B]                                        
Hit http://ddebs.ubuntu.com karmic/multiverse Packages                                           
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                                       
Hit http://ppa.launchpad.net jaunty Release.gpg                            
Ign http://archive.ubuntu.com karmic-backports/restricted Translation-en_US
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                 
Ign http://archive.ubuntu.com karmic-backports/main Translation-en_US      
Hit http://ppa.launchpad.net karmic Release.gpg                            
Ign http://archive.ubuntu.com karmic-backports/multiverse Translation-en_US
Ign http://ppa.launchpad.net karmic/main Translation-en_US                 
Hit http://ppa.launchpad.net karmic Release.gpg                            
Ign http://archive.ubuntu.com karmic-backports/universe Translation-en_US  
Get:8 http://archive.ubuntu.com karmic-proposed Release.gpg [189B]         
Ign http://ppa.launchpad.net karmic/main Translation-en_US                 
Get:9 http://ppa.launchpad.net karmic Release.gpg [307B]                   
Ign http://archive.ubuntu.com karmic-proposed/restricted Translation-en_US 
Ign http://archive.ubuntu.com karmic-proposed/main Translation-en_US                                   
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                             
Ign http://archive.ubuntu.com karmic-proposed/multiverse Translation-en_US 
Hit http://ppa.launchpad.net karmic Release.gpg                            
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                             
Hit http://ppa.launchpad.net karmic Release.gpg                                                        
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                             
Ign http://ppa.launchpad.net karmic Release.gpg                                                        
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                             
Hit http://ppa.launchpad.net jaunty Release                                                            
Hit http://ppa.launchpad.net jaunty Release                                                                
Ign http://archive.ubuntu.com karmic-proposed/universe Translation-en_US                                   
Hit http://ppa.launchpad.net jaunty Release                                                                
Hit http://archive.ubuntu.com karmic Release                                                               
Get:10 http://ppa.launchpad.net karmic Release [66.0kB]                                                    
Hit http://archive.ubuntu.com karmic-updates Release                                                       
Hit http://archive.ubuntu.com karmic-security Release                                                      
Get:11 http://archive.ubuntu.com karmic-backports Release [41.7kB]                                         
Ign http://archive.ubuntu.com karmic-backports Release                                                     
Hit http://ppa.launchpad.net jaunty Release                                                                
Get:12 http://archive.ubuntu.com karmic-proposed Release [41.7kB]                                          
Hit http://ppa.launchpad.net jaunty Release                                                                
Ign http://archive.ubuntu.com karmic-proposed Release                                                      
Hit http://ppa.launchpad.net jaunty Release                                                                
Hit http://archive.ubuntu.com karmic/main Packages                                                         
Hit http://ppa.launchpad.net jaunty Release                                                                
Hit http://archive.ubuntu.com karmic/restricted Packages                                                   
Hit http://ppa.launchpad.net jaunty Release                                                                
Hit http://ppa.launchpad.net karmic Release                                                                
Hit http://ppa.launchpad.net karmic Release                                                                
Hit http://archive.ubuntu.com karmic/main Sources                                               
Get:13 http://ppa.launchpad.net karmic Release [66.0kB]                                                    
Ign http://ppa.launchpad.net karmic Release                                                                
Hit http://ppa.launchpad.net karmic Release                                                                
Hit http://archive.ubuntu.com karmic/restricted Sources                                                    
Hit http://ppa.launchpad.net karmic Release                                                                
Hit http://archive.ubuntu.com karmic/universe Packages                                                     
Hit http://archive.ubuntu.com karmic/universe Sources                                                      
Hit http://archive.ubuntu.com karmic/multiverse Packages                                                   
Hit http://archive.ubuntu.com karmic/multiverse Sources                                                    
Hit http://archive.ubuntu.com karmic-updates/main Packages                                                 
Hit http://archive.ubuntu.com karmic-updates/restricted Packages                                           
Hit http://archive.ubuntu.com karmic-updates/main Sources                                                  
Hit http://archive.ubuntu.com karmic-updates/restricted Sources                                            
Ign http://ppa.launchpad.net karmic Release                                                                
Hit http://archive.ubuntu.com karmic-updates/universe Packages                                             
Hit http://archive.ubuntu.com karmic-updates/universe Sources                                              
Hit http://archive.ubuntu.com karmic-updates/multiverse Packages                                       
Hit http://archive.ubuntu.com karmic-updates/multiverse Sources                                        
Hit http://archive.ubuntu.com karmic-security/main Packages                                            
Hit http://archive.ubuntu.com karmic-security/restricted Packages                                      
Hit http://ppa.launchpad.net jaunty/main Packages                                                      
Hit http://archive.ubuntu.com karmic-security/main Sources                                                 
Hit http://ppa.launchpad.net jaunty/main Sources                                                           
Hit http://archive.ubuntu.com karmic-security/restricted Sources                                           
Hit http://ppa.launchpad.net jaunty/main Packages                                                          
Hit http://archive.ubuntu.com karmic-security/universe Packages                                            
Hit http://ppa.launchpad.net jaunty/main Packages                                                          
Hit http://archive.ubuntu.com karmic-security/universe Sources                                             
Get:14 http://ppa.launchpad.net karmic/main Packages [8,914B]                                              
Hit http://archive.ubuntu.com karmic-security/multiverse Packages                                          
Hit http://ppa.launchpad.net jaunty/main Packages                                                          
Hit http://archive.ubuntu.com karmic-security/multiverse Sources                                           
Hit http://ppa.launchpad.net jaunty/main Packages                                                          
Hit http://archive.ubuntu.com karmic-backports/restricted Packages                                         
Hit http://ppa.launchpad.net jaunty/main Sources                                                           
Hit http://ppa.launchpad.net jaunty/main Packages                                                          
Hit http://archive.ubuntu.com karmic-backports/main Packages                                               
Hit http://ppa.launchpad.net jaunty/main Sources                                                           
Hit http://archive.ubuntu.com karmic-backports/multiverse Packages                                         
Hit http://ppa.launchpad.net jaunty/main Packages                                                          
Hit http://archive.ubuntu.com karmic-backports/universe Packages                                           
Hit http://ppa.launchpad.net jaunty/main Sources                                                           
Hit http://archive.ubuntu.com karmic-proposed/restricted Packages                                          
Hit http://ppa.launchpad.net jaunty/main Packages                                                          
Hit http://archive.ubuntu.com karmic-proposed/main Packages                                                
Hit http://ppa.launchpad.net jaunty/main Sources                                                           
Hit http://ppa.launchpad.net karmic/main Packages                                                          
Hit http://archive.ubuntu.com karmic-proposed/multiverse Packages                                          
Hit http://archive.ubuntu.com karmic-proposed/universe Packages                                            
Hit http://ppa.launchpad.net karmic/main Sources                                                           
Hit http://ppa.launchpad.net karmic/main Packages                                                          
Hit http://ppa.launchpad.net karmic/main Sources                                                           
Hit http://ppa.launchpad.net karmic/main Packages                                                          
Hit http://ppa.launchpad.net karmic/main Packages                                                          
Hit http://ppa.launchpad.net karmic/main Packages                                                          
Ign http://ppa.launchpad.net karmic/main Packages                                                          
Ign http://ppa.launchpad.net karmic/main Packages                                                          
Err http://ppa.launchpad.net karmic/main Packages                                                          
  404  Not Found
Fetched 79.5kB in 12s (6,129B/s)                                                                           
W: GPG error: http://download.virtualbox.org jaunty Release: The following signatures were invalid: BADSIG DCF9F87B6DFBCBAE Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>
W: GPG error: http://archive.ubuntu.com karmic-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com karmic-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures were invalid: BADSIG 7FB8BEE0A1F196A8 Launchpad PPA for Pidgin Developers
W: Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Sand &amp; Mercury on 2009-09-30
^ It's a fault on the end of the launchpad key server, I believe. They've been having problems lately. Running Jaunty myself, I've noticed that as well.

---

### Post by Longinus00 on 2009-10-01
Launchpad might be having some adjusting pains from changing to the new design. I know I've experienced very slow access and many timeouts in the past week or so.

---

### Post by deathsshadow77 on 2009-10-01
Doesn't it automatically add the keys in karmic? I added a ppa in software sources and the key is there in the authentication tab. I didn't have to add anything.

---

