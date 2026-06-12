---
title: "Unable to use PPA"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by vigs on 2011-01-30
I have added the LibreOffice PPA (ppa:libreoffice/ppa) and when I do a ```
sudo apt-get update
``` the update just ignores the PPA (relevant lines below):
```
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en                                                      
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en_IN
```
SO when I do a ```
sudo apt-get install libreoffice
``` it says:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libreoffice
```
Any solution?

---

### Post by davidmohammed on 2011-01-30
any errors reported if you run the following

sudo apt-get update && sudo apt-get upgrade

?

---

### Post by vigs on 2011-01-30
YES
```

$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for vighnesh: 
Hit http://extras.ubuntu.com maverick Release.gpg
Hit http://archive.canonical.com maverick Release.gpg                                                                                 
Get:1 http://ppa.launchpad.net maverick Release.gpg [316B]                                                                            
Get:2 http://mirror.cse.iitk.ac.in maverick Release.gpg [198B]                                                                         
Ign http://ppa.launchpad.net/clicompanion-devs/clicompanion-nightlies/ubuntu/ maverick/main Translation-en                                      
Hit http://linux.dropbox.com maverick Release.gpg                                                                                      
Ign http://dl.google.com stable Release.gpg                                                                                            
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en                                                                  
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_IN                                                                                    
Ign http://dl.google.com stable Release.gpg                                                                                                                 
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en                                                                                   
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_IN                                     
Ign http://dl.google.com stable Release                                                                                                                     
Ign http://dl.google.com stable Release                                                                                                                     
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                                                     
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                                                     
Ign http://dl.google.com stable/main i386 Packages                                                               
Ign http://dl.google.com stable/main i386 Packages                                                               
Ign http://dl.google.com stable/main i386 Packages                                                               
Ign http://dl.google.com stable/main i386 Packages                                                               
Err http://dl.google.com stable/main i386 Packages                                                               
  503  Service Unavailable
Err http://dl.google.com stable/main i386 Packages                                                               
  503  Service Unavailable
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/main Translation-en                                            
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/main Translation-en_IN                                         
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/multiverse Translation-en                                      
Ign http://ppa.launchpad.net/clicompanion-devs/clicompanion-nightlies/ubuntu/ maverick/main Translation-en_IN    
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/multiverse Translation-en_IN                                   
Get:3 http://ppa.launchpad.net maverick Release.gpg [316B]                                                       
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/restricted Translation-en                                      
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ maverick/main Translation-en                              
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ maverick/main Translation-en_IN                           
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/restricted Translation-en_IN                                   
Get:4 http://ppa.launchpad.net maverick Release.gpg [316B]                                                       
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/universe Translation-en                                        
Ign http://ppa.launchpad.net/doctormo/ppa/ubuntu/ maverick/main Translation-en                                   
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/universe Translation-en_IN                                     
Ign http://ppa.launchpad.net/doctormo/ppa/ubuntu/ maverick/main Translation-en_IN                                
Get:5 http://mirror.cse.iitk.ac.in maverick-updates Release.gpg [198B]                                           
Get:6 http://ppa.launchpad.net maverick Release.gpg [316B]                                                       
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en                                    
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/main Translation-en                                    
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en_IN                                 
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/main Translation-en_IN                                 
Get:7 http://ppa.launchpad.net maverick Release.gpg [316B]                                                       
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/multiverse Translation-en                              
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ maverick/main Translation-en                              
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ maverick/main Translation-en_IN                           
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/multiverse Translation-en_IN                           
Get:8 http://ppa.launchpad.net maverick Release.gpg [316B]                                                       
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/restricted Translation-en                              
Ign http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/ maverick/main Translation-en                      
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/restricted Translation-en_IN                           
Ign http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/ maverick/main Translation-en_IN                   
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/universe Translation-en          
Get:9 http://ppa.launchpad.net maverick Release.gpg [316B]                                                                                 
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en                                                          
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en_IN                             
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/universe Translation-en_IN                             
Get:10 http://ppa.launchpad.net maverick Release.gpg [316B]                                                      
Ign http://mirror.cse.iitk.ac.in maverick-security Release.gpg                                                   
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en                           
Get:11 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/main Translation-en [198B]                         
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en_IN                                                     
98% [11 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/main Translation-en                                                                
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                             
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/main Translation-en_IN                                                                           
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/multiverse Translation-en                                                                        
Get:12 http://ppa.launchpad.net/norsetto/ppa/ubuntu/ maverick/main Translation-en [9,749B]                                                                  
98% [12 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]     479B/s 0sbzip2: (stdin) is not a bzip2 file.
Ign http://ppa.launchpad.net/norsetto/ppa/ubuntu/ maverick/main Translation-en                                                                              
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/multiverse Translation-en_IN                                                                     
Hit http://ppa.launchpad.net/norsetto/ppa/ubuntu/ maverick/main Translation-en_IN                                                                           
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/restricted Translation-en                                                                        
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                           
Hit http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en                                                                           
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/restricted Translation-en_IN                                                                     
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/universe Translation-en                                                                          
Get:13 http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en_IN [9,758B]                                                            
56% [13 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en_IN                                                             
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/universe Translation-en_IN                                                                       
Ign http://mirror.cse.iitk.ac.in maverick-proposed Release.gpg                                                                                              
Get:14 http://ppa.launchpad.net maverick Release.gpg [9,732B]                                                                                               
Get:15 http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en [9,745B]                                                                 
53% [15 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]    479B/s 41sbzip2: (stdin) is not a bzip2 file.
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en                                                                             
Get:16 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/main Translation-en [198B]                                                                    
30% [16 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/main Translation-en                                                                
Get:17 http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_IN [57.3kB]                                                              
70% [17 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_IN                                                               
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/main Translation-en_IN                                                                           
Hit http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/multiverse Translation-en                                                                        
Get:18 http://ppa.launchpad.net maverick Release [9,750B]                                                                                                   
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/multiverse Translation-en_IN                                                                     
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/restricted Translation-en                                                                        
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/restricted Translation-en_IN                                                                     
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/universe Translation-en                                                                          
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/universe Translation-en_IN                                                                       
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://mirror.cse.iitk.ac.in maverick-backports Release.gpg                                                                                             
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                           
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                                                    
Get:19 http://ppa.launchpad.net maverick/main Sources/DiffIndex [473B]                                                                                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_IN                                                                                        
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_IN                                                                                 
Get:20 http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex [445B]                                                                                
Hit http://extras.ubuntu.com maverick Release                                                                                                               
Hit http://archive.canonical.com maverick Release                                                                                                           
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en                                                                                           
Get:21 http://ppa.launchpad.net maverick/main Sources/DiffIndex [3,939B]                                                                                    
Hit http://extras.ubuntu.com maverick/main i386 Packages                                                                                                    
Hit http://archive.canonical.com maverick/partner Sources                                                                                                   
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_IN                                                                                        
Hit http://archive.canonical.com maverick/partner i386 Packages                                                                                             
Get:22 http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex [22.5kB]                                                                              
Hit http://linux.dropbox.com maverick Release                                                                                                               
Get:23 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/main Translation-en [39.8kB]                                                                 
35% [23 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]                                           479B/s 3min 58sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/main Translation-en                                                                             
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                                                                                
Hit http://linux.dropbox.com maverick/main i386 Packages                                                                                                    
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex                                                                                          
Get:24 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/main Translation-en_IN [31.4kB]                                                              
25% [24 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers]                                                                 3,178B/s 48sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/main Translation-en_IN                                                                          
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex                                                                                          
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                                                                                
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex                                                                                          
Get:25 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/multiverse Translation-en [31.4kB]                                                           
22% [25 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers]                                                                    3,178B/s 58sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/multiverse Translation-en                                                                       
Ign http://ppa.launchpad.net maverick/main Sources                                                                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                                    
Get:26 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/multiverse Translation-en_IN [31.4kB]                                                        
19% [26 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers]                                                             3,178B/s 1min 8sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/multiverse Translation-en_IN                                                                    
Hit http://ppa.launchpad.net maverick/main Sources                                                                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                                    
Get:27 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/restricted Translation-en [23.2kB]                                                           
15% [27 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers]                                                               3,178B/s 1min 18sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/restricted Translation-en                                                                       
Hit http://ppa.launchpad.net maverick/main Sources/DiffIndex                                                                                                
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 41FDF8A2B455BEF0 Launchpad clicompanion-nightlies    
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFF96872D340A3
E: Could not open file /var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_maverick_main_source_Sources.IndexDiff - open (2: No such file or directory)

```

---

### Post by davidmohammed on 2011-01-30
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)

you've probably got update manager or synaptic manager open.  Suggest close it.


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 41FDF8A2B455BEF0 Launchpad clicompanion-nightlies    

suggest temporarily untick the clicompanion-nightlies ppa from software-sources (upgrade manager - settings...)

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFF96872D340A3

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D0AFF96872D340A3

---

### Post by vigs on 2011-01-30
Ya I did that.
Now I get even more warnings and errors :(
```
$ sudo apt-get update
Ign http://dl.google.com stable Release.gpg
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en                                                                              
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_IN                                                                           
Ign http://dl.google.com stable Release.gpg                                                                                                                 
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en                                                                                   
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_IN                                                                                
Ign http://dl.google.com stable Release                                                                                                                     
Ign http://dl.google.com stable Release                                                                                                                     
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                                                    
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                                                    
Ign http://dl.google.com stable/main i386 Packages                                                              
Ign http://dl.google.com stable/main i386 Packages                                                              
Ign http://dl.google.com stable/main i386 Packages                                                              
Ign http://dl.google.com stable/main i386 Packages                                                              
Err http://dl.google.com stable/main i386 Packages                                                              
  503  Service Unavailable
Err http://dl.google.com stable/main i386 Packages                                                              
  503  Service Unavailable
Hit http://ppa.launchpad.net maverick Release.gpg                                                               
Hit http://extras.ubuntu.com maverick Release.gpg                                                               
Hit http://archive.canonical.com maverick Release.gpg                                      
Get:1 http://mirror.cse.iitk.ac.in maverick Release.gpg [198B]                                                   
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ maverick/main Translation-en                              
Hit http://linux.dropbox.com maverick Release.gpg                                                                
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/main Translation-en                                            
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ maverick/main Translation-en_IN                           
Get:2 http://ppa.launchpad.net maverick Release.gpg [316B]                                 
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/main Translation-en_IN                                         
Ign http://ppa.launchpad.net/doctormo/ppa/ubuntu/ maverick/main Translation-en                                   
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/multiverse Translation-en                
Ign http://ppa.launchpad.net/doctormo/ppa/ubuntu/ maverick/main Translation-en_IN          
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/multiverse Translation-en_IN                                   
Get:3 http://ppa.launchpad.net maverick Release.gpg [316B]                                                       
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en                                             
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/restricted Translation-en                                      
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en_IN           
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/restricted Translation-en_IN             
Get:4 http://ppa.launchpad.net maverick Release.gpg [316B]                                 
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/universe Translation-en                                                 
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ maverick/main Translation-en        
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick/universe Translation-en_IN               
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ maverick/main Translation-en_IN     
Get:5 http://ppa.launchpad.net maverick Release.gpg [316B]                                                       
Get:6 http://mirror.cse.iitk.ac.in maverick-updates Release.gpg [198B]                                           
Ign http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/ maverick/main Translation-en                      
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/main Translation-en                                    
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/main Translation-en_IN           
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/multiverse Translation-en        
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/multiverse Translation-en_IN     
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/restricted Translation-en        
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/restricted Translation-en_IN                           
Ign http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/ maverick/main Translation-en_IN                   
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/universe Translation-en                                
Get:7 http://ppa.launchpad.net maverick Release.gpg [316B]                                 
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en                                
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en_IN                             
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-updates/universe Translation-en_IN       
Hit http://ppa.launchpad.net maverick Release.gpg                                                                
Ign http://mirror.cse.iitk.ac.in maverick-security Release.gpg                                                   
Hit http://ppa.launchpad.net/norsetto/ppa/ubuntu/ maverick/main Translation-en             
Get:8 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/main Translation-en [198B]    
Hit http://ppa.launchpad.net/norsetto/ppa/ubuntu/ maverick/main Translation-en_IN                                                            
97% [8 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/main Translation-en                                                               
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                            
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/main Translation-en_IN                                                                           
Get:9 http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en [9,758B]                                                                
97% [9 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]      323B/s 0sbzip2: (stdin) is not a bzip2 file.
Ign http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en                                                                           
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/multiverse Translation-en                                                                        
Get:10 http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en_IN [9,732B]                                                            
54% [10 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en_IN                                                             
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/multiverse Translation-en_IN                                                                     
Get:11 http://ppa.launchpad.net maverick Release.gpg [57.3kB]                                                                                               
Hit http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en                                                                             
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/restricted Translation-en                                                                        
Get:12 http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_IN [9,750B]                                                              
77% [12 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_IN                                                               
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/restricted Translation-en_IN                                                                     
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/universe Translation-en                                                                          
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-security/universe Translation-en_IN                                                                       
Ign http://mirror.cse.iitk.ac.in maverick-proposed Release.gpg                                                                                              
Get:13 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/main Translation-en [198B]                                                                    
66% [13 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/main Translation-en                                                                
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/main Translation-en_IN                                                                           
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/multiverse Translation-en                                                                        
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/multiverse Translation-en_IN                                                                     
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/restricted Translation-en                                                                        
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/restricted Translation-en_IN                                                                     
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/universe Translation-en                                                                          
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-proposed/universe Translation-en_IN                                                                       
Ign http://mirror.cse.iitk.ac.in maverick-backports Release.gpg                                                                                             
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                                                    
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                           
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_IN                                                                                 
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_IN                                                                                        
Hit http://archive.canonical.com maverick Release                                                                                                           
Hit http://extras.ubuntu.com maverick Release                                                                                                               
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en                                                                                           
Hit http://archive.canonical.com maverick/partner Sources                                                                                                   
Hit http://extras.ubuntu.com maverick/main i386 Packages                                                                                                    
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_IN                                                                                        
Hit http://archive.canonical.com maverick/partner i386 Packages                                                                                             
Get:14 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/main Translation-en [39.8kB]                                                                 
76% [14 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]                                           323B/s 1min 31sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/main Translation-en                                                                             
Hit http://linux.dropbox.com maverick Release                                                                                                               
Hit http://linux.dropbox.com maverick/main i386 Packages                                                                                                    
Get:15 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/main Translation-en_IN [31.4kB]                                                              
56% [15 Translation-en_IN bzip2 0B] [Waiting for headers] [Waiting for headers]                                                                  9,319B/s 7sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/main Translation-en_IN                                                                          
Get:16 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/multiverse Translation-en [31.4kB]                                                           
47% [16 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers]                                                                    9,319B/s 10sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/multiverse Translation-en                                                                       
Get:17 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/multiverse Translation-en_IN [31.4kB]                                                        
40% [17 Translation-en_IN bzip2 0B] [Waiting for headers]                                                                                       9,319B/s 14sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/multiverse Translation-en_IN                                                                    
Get:18 http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/restricted Translation-en [23.2kB]                                                           
33% [18 Translation-en bzip2 0B] [Waiting for headers] [Waiting for headers]                                                                    9,319B/s 17sbzip2: (stdin) is not a bzip2 file.
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/restricted Translation-en                                                                       
Hit http://ppa.launchpad.net maverick Release                                                                                                               
Hit http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Hit http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Hit http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Get:19 http://ppa.launchpad.net maverick Release [9,758B]                                                                                                   
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Get:20 http://ppa.launchpad.net maverick Release [9,732B]                                                                                                   
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Get:21 http://ppa.launchpad.net maverick Release [57.3kB]                                                                                                   
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Hit http://ppa.launchpad.net maverick Release                                                                                                               
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Get:22 http://ppa.launchpad.net maverick Release [9,750B]                                                                                                   
Ign http://ppa.launchpad.net maverick Release                                                                                                               
Hit http://ppa.launchpad.net maverick/main Sources                                                                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                                    
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                                                                                
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex                                                                                          
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex                                                                                          
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                                                                                
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex                                                                                          
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                                                                                
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex                                                                                          
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                                                                                
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex                                                                                          
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                                                                                
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex                                                                                          
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex                                                                                          
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex                                                                                          
Hit http://ppa.launchpad.net maverick/main Sources                                                                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                                    
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                                    
Hit http://ppa.launchpad.net maverick/main Sources                                                                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                                    
Hit http://ppa.launchpad.net maverick/main Sources                                                                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                                    
Hit http://ppa.launchpad.net maverick/main Sources                                                                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                                    
Hit http://ppa.launchpad.net maverick/main Sources                                                                                                          
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/restricted Translation-en_IN                                                                    
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                                    
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/universe Translation-en                                                                         
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                                    
Ign http://mirror.cse.iitk.ac.in/ubuntu/ maverick-backports/universe Translation-en_IN                                                                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                                    
Get:23 http://mirror.cse.iitk.ac.in maverick Release [39.8kB]                                                                                               
Get:24 http://mirror.cse.iitk.ac.in maverick-updates Release [31.4kB]                                                                                       
Ign http://mirror.cse.iitk.ac.in maverick-updates Release                                                                                                   
Get:25 http://mirror.cse.iitk.ac.in maverick-security Release [31.4kB]                                                                                      
Get:26 http://mirror.cse.iitk.ac.in maverick-proposed Release [31.4kB]                                                                                      
Get:27 http://mirror.cse.iitk.ac.in maverick-backports Release [23.2kB]                                                                                     
Get:28 http://mirror.cse.iitk.ac.in maverick/main Sources [829kB]                                                                                           
Get:29 http://mirror.cse.iitk.ac.in maverick/restricted Sources [4,370B]                                                                                    
Get:30 http://mirror.cse.iitk.ac.in maverick/multiverse Sources [151kB]                                                                                     
Get:31 http://mirror.cse.iitk.ac.in maverick/universe Sources [4,179kB]                                                                                     
Get:32 http://mirror.cse.iitk.ac.in maverick/main i386 Packages [1,492kB]                                                                                   
Get:33 http://mirror.cse.iitk.ac.in maverick/restricted i386 Packages [5,992B]                                                                              
Get:34 http://mirror.cse.iitk.ac.in maverick/universe i386 Packages [5,791kB]                                                                               
Get:35 http://mirror.cse.iitk.ac.in maverick/multiverse i386 Packages [183kB]                                                                               
Ign http://mirror.cse.iitk.ac.in maverick-updates/restricted Sources/DiffIndex                                                                              
Ign http://mirror.cse.iitk.ac.in maverick-updates/main Sources/DiffIndex                                                                                    
Ign http://mirror.cse.iitk.ac.in maverick-updates/multiverse Sources/DiffIndex                                                                              
Ign http://mirror.cse.iitk.ac.in maverick-updates/universe Sources/DiffIndex                                                                                
Ign http://mirror.cse.iitk.ac.in maverick-updates/main i386 Packages/DiffIndex                                                                              
Ign http://mirror.cse.iitk.ac.in maverick-updates/restricted i386 Packages/DiffIndex                                                                        
Ign http://mirror.cse.iitk.ac.in maverick-updates/universe i386 Packages/DiffIndex                                                                          
Ign http://mirror.cse.iitk.ac.in maverick-updates/multiverse i386 Packages/DiffIndex                                                                        
Ign http://mirror.cse.iitk.ac.in maverick-security/restricted Sources/DiffIndex                                                                             
Ign http://mirror.cse.iitk.ac.in maverick-security/main Sources/DiffIndex                                                                                   
Ign http://mirror.cse.iitk.ac.in maverick-security/multiverse Sources/DiffIndex                                                                             
Ign http://mirror.cse.iitk.ac.in maverick-security/universe Sources/DiffIndex                                                                               
Ign http://mirror.cse.iitk.ac.in maverick-security/main i386 Packages/DiffIndex                                                                             
Ign http://mirror.cse.iitk.ac.in maverick-security/restricted i386 Packages/DiffIndex                                                                       
Ign http://mirror.cse.iitk.ac.in maverick-security/universe i386 Packages/DiffIndex                                                                         
Ign http://mirror.cse.iitk.ac.in maverick-security/multiverse i386 Packages/DiffIndex                                                                       
Ign http://mirror.cse.iitk.ac.in maverick-proposed/restricted Sources/DiffIndex                                                                             
Ign http://mirror.cse.iitk.ac.in maverick-proposed/main Sources/DiffIndex                                                                                   
Ign http://mirror.cse.iitk.ac.in maverick-proposed/multiverse Sources/DiffIndex                                                                             
Ign http://mirror.cse.iitk.ac.in maverick-proposed/universe Sources/DiffIndex                                                                               
Ign http://mirror.cse.iitk.ac.in maverick-proposed/restricted i386 Packages/DiffIndex                                                                       
Ign http://mirror.cse.iitk.ac.in maverick-proposed/main i386 Packages/DiffIndex                                                                             
Ign http://mirror.cse.iitk.ac.in maverick-proposed/multiverse i386 Packages/DiffIndex                                                                       
Ign http://mirror.cse.iitk.ac.in maverick-proposed/universe i386 Packages/DiffIndex                                                                         
Ign http://mirror.cse.iitk.ac.in maverick-backports/restricted Sources/DiffIndex                                                                            
Ign http://mirror.cse.iitk.ac.in maverick-backports/main Sources/DiffIndex                                                                                  
Ign http://mirror.cse.iitk.ac.in maverick-backports/multiverse Sources/DiffIndex                                                                            
Ign http://mirror.cse.iitk.ac.in maverick-backports/universe Sources/DiffIndex                                                                              
Ign http://mirror.cse.iitk.ac.in maverick-backports/restricted i386 Packages/DiffIndex                                                                      
Ign http://mirror.cse.iitk.ac.in maverick-backports/main i386 Packages/DiffIndex                                                                            
Ign http://mirror.cse.iitk.ac.in maverick-backports/multiverse i386 Packages/DiffIndex                                                                      
Ign http://mirror.cse.iitk.ac.in maverick-backports/universe i386 Packages/DiffIndex                                                                        
Get:36 http://mirror.cse.iitk.ac.in maverick-updates/restricted Sources [778B]                                                                              
Get:37 http://mirror.cse.iitk.ac.in maverick-updates/main Sources [77.9kB]                                                                                  
Get:38 http://mirror.cse.iitk.ac.in maverick-updates/multiverse Sources [1,504B]                                                                            
Get:39 http://mirror.cse.iitk.ac.in maverick-updates/universe Sources [27.4kB]                                                                              
Get:40 http://mirror.cse.iitk.ac.in maverick-updates/main i386 Packages [213kB]                                                                             
Get:41 http://mirror.cse.iitk.ac.in maverick-updates/restricted i386 Packages [1,797B]                                                                      
Get:42 http://mirror.cse.iitk.ac.in maverick-updates/universe i386 Packages [85.1kB]                                                                        
Get:43 http://mirror.cse.iitk.ac.in maverick-updates/multiverse i386 Packages [2,836B]                                                                      
Get:44 http://mirror.cse.iitk.ac.in maverick-security/restricted Sources [14B]                                                                              
Get:45 http://mirror.cse.iitk.ac.in maverick-security/main Sources [23.1kB]                                                                                 
Get:46 http://mirror.cse.iitk.ac.in maverick-security/multiverse Sources [649B]                                                                             
Get:47 http://mirror.cse.iitk.ac.in maverick-security/universe Sources [9,802B]                                                                             
Get:48 http://mirror.cse.iitk.ac.in maverick-security/main i386 Packages [75.0kB]                                                                           
Get:49 http://mirror.cse.iitk.ac.in maverick-security/restricted i386 Packages [14B]                                                                        
Get:50 http://mirror.cse.iitk.ac.in maverick-security/universe i386 Packages [38.5kB]                                                                       
Get:51 http://mirror.cse.iitk.ac.in maverick-security/multiverse i386 Packages [1,655B]                                                                     
Get:52 http://mirror.cse.iitk.ac.in maverick-proposed/restricted Sources [14B]                                                                              
Get:53 http://mirror.cse.iitk.ac.in maverick-proposed/main Sources [14.3kB]                                                                                 
Get:54 http://mirror.cse.iitk.ac.in maverick-proposed/multiverse Sources [640B]                                                                             
Get:55 http://mirror.cse.iitk.ac.in maverick-proposed/universe Sources [5,594B]                                                                             
Get:56 http://mirror.cse.iitk.ac.in maverick-proposed/restricted i386 Packages [14B]                                                                        
Get:57 http://mirror.cse.iitk.ac.in maverick-proposed/main i386 Packages [25.0kB]                                                                           
Get:58 http://mirror.cse.iitk.ac.in maverick-proposed/multiverse i386 Packages [1,124B]                                                                     
Get:59 http://mirror.cse.iitk.ac.in maverick-proposed/universe i386 Packages [14.3kB]                                                                       
Get:60 http://mirror.cse.iitk.ac.in maverick-backports/restricted Sources [14B]                                                                             
Get:61 http://mirror.cse.iitk.ac.in maverick-backports/main Sources [921B]                                                                                  
Get:62 http://mirror.cse.iitk.ac.in maverick-backports/multiverse Sources [14B]                                                                             
Get:63 http://mirror.cse.iitk.ac.in maverick-backports/universe Sources [3,287B]                                                                            
Get:64 http://mirror.cse.iitk.ac.in maverick-backports/restricted i386 Packages [14B]                                                                       
Get:65 http://mirror.cse.iitk.ac.in maverick-backports/main i386 Packages [1,894B]                                                                          
Get:66 http://mirror.cse.iitk.ac.in maverick-backports/multiverse i386 Packages [14B]                                                                       
Get:67 http://mirror.cse.iitk.ac.in maverick-backports/universe i386 Packages [6,258B]                                                                      
Fetched 13.6MB in 2min 0s (113kB/s)                                                                                                                         
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 44270923C32A36BF
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG C41B720D95628707 Launchpad PPA for Cesare Tirabassi
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG F58DBE6EA8DF5CE3 Launchpad pdfmod
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX
W: GPG error: http://ppa.launchpad.net maverick Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net maverick Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: NODATA 3 NODATA 4
W: GPG error: http://mirror.cse.iitk.ac.in maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://ppa.launchpad.net/norsetto/ppa/ubuntu/dists/maverick/Release.gpg  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ppa.launchpad.net_norsetto_ppa_ubuntu_dists_maverick_Release.gpg).

W: Failed to fetch http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/dists/maverick/Release.gpg  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ppa.launchpad.net_pdfmod-team_ppa_ubuntu_dists_maverick_Release.gpg).

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz  503  Service Unavailable

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages.gz  503  Service Unavailable

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by davidmohammed on 2011-01-30
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 44270923C32A36BF

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 44270923C32A36BF

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 83FBA1751378B444

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG C41B720D95628707 Launchpad PPA for Cesare Tirabassi

untick this ppa from software sources

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG F58DBE6EA8DF5CE3 Launchpad pdfmod

untick this ppa from software sources

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX

untick this ppa from software sources

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: Unknown error executing gpgv
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: Unknown error executing gpgv
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: NODATA 3 NODATA 4
W: GPG error: [http://mirror.cse.iitk.ac.in](http://mirror.cse.iitk.ac.in) maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

untick this one from software sources

W: Failed to fetch [http://ppa.launchpad.net/norsetto/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/norsetto/ppa/ubuntu/dists/maverick/Release.gpg)  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ppa.launchpad.net_norsetto_ppa_ubuntu_dists_maverick_Release.gpg).

W: Failed to fetch [http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/dists/maverick/Release.gpg)  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ppa.launchpad.net_pdfmod-team_ppa_ubuntu_dists_maverick_Release.gpg).

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz)  503  Service Unavailable

untick this one from software sources

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages.gz](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages.gz)  503  Service Unavailable

untick this one from software sources

---

