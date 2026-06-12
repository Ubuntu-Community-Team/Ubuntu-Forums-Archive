---
title: "Help with Add/Remove programs!!"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by Kanetakerus on 2007-03-23
Problem: Add/remove programs quits without error message

I know this has been posted before, however nothing in any of the other threads seemed to work for me. I know that the file causing this problem is sources.list

I locate the file in /etc/apt/sources.list
When I open it, up comes the text editor, but the strange thing is, its blank, theres no text at all!
Plus it only permits me to read, therefore I cant enter text and save the file.

As you can see I am a n000b to linux :neutral:

Any help would be much appreiciated

---

### Post by akudewan on 2007-03-23
You'll have to open a terminal and type this: ```
 sudo gedit /etc/apt/sources.list 
```. Then enter your password.

You'll be able to add the sources and save the file after this.

---

### Post by pradeepadapa on 2007-03-23
hello man,

shuld we change the http infront of the sites present in sources.lst to ftp or not,

since http is not working fr update in add/remove or in 
sudo apt-get update

what shuld we do /...

---

### Post by pradeepadapa on 2007-03-23
[size +4] can anyone help [/size]

---

### Post by akudewan on 2007-03-23
> **pradeepadapa said:**
> hello man,

shuld we change the http infront of the sites present in sources.lst to ftp or not,

since http is not working fr update in add/remove or in 
sudo apt-get update

what shuld we do /...

http works just fine. What exactly are the error messages you're getting?

---

### Post by mcduck on 2007-03-23
> **akudewan said:**
> You'll have to open a terminal and type this: ```
 sudo gedit /etc/apt/sources.list 
```. Then enter your password.

You'll be able to add the sources and save the file after this.

Better make it 'gksudo gedit /etc/apt/sources.list'. You should always ude gksudo for GUI applications, as 'sudo' doesn't load root user's desktop profile but uses your's instead, which might in same cases break your desktop configurations..

'sudo' for CLI apps, 'gksudo' for GUI apps. :)

---

### Post by pradeepadapa on 2007-03-23
[SIZE="2"]my command to update the apt

$sudo apt-get update                 ,the result is as shown below-----------------


Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                   
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Get:3 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US             
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/universe Translation-en_US      
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US     
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security/restricted Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-proposed/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources               
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages [162kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security/universe Packages               
99% [8 Packages gzip 0] [Waiting for headers] [Connecting to packages.freecontr
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                      
  Sub-process gzip returned an error code (1)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-security/multiverse Packages             
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages [162kB]            
99% [9 Packages gzip 0] [Connecting to packages.freecontrib.org (88.191.33.6)] 
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages                      
  Sub-process gzip returned an error code (1)
Get:10 [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release.gpg [191B]                   
Ign [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main/easyubuntu Translation-en_US            
Hit [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release                                 
Hit [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main/easyubuntu Packages                     
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg                                                                
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.95), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy Release.gpg                                                            
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                                                     
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.95), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/free Translation-en_US                                                 
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/non-free Translation-en_US
  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Fetched 10B in 6m0s (0B/s)                                
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/i18n/Translation-en_US.bz2)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/i18n/Translation-en_US.bz2)  Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/Release.gpg](http://www.getautomatix.com/apt/dists/edgy/Release.gpg)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.95), connection timed out
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2](http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.95), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.[/SIZE]

[SIZE="4"]now how can i rectify this problem[/SIZE]

---

### Post by Kanetakerus on 2007-03-23
> **mcduck said:**
> Better make it 'gksudo gedit /etc/apt/sources.list'. You should always ude gksudo for GUI applications, as 'sudo' doesn't load root user's desktop profile but uses your's instead, which might in same cases break your desktop configurations..

'sudo' for CLI apps, 'gksudo' for GUI apps. :)

Hey thanks alot! Problem solved :)

---

