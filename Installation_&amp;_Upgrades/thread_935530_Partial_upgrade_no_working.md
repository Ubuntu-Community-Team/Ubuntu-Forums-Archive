---
title: "Partial upgrade no working"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by billio on 2008-10-01
I keep being asked to upgrade (currently 8.04.1), at the moment I have 999 packages to update.

It responds that only a partial upgrade can be performed, and then when this is selected nothing is upgraded as the security check fail.

Can anyone explain ?.

Bill

---

### Post by Pumalite on 2008-10-01
could you post:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by billio on 2008-10-02
Thanks for the response.

Here you are 
----------------
billo@lenovo:~$ sudo apt-get update
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB                  
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release.gpg                                
Get: 1 [http://ftp.uk.debian.org](http://ftp.uk.debian.org) sid Release.gpg [189B]                         
Ign [http://ftp.uk.debian.org](http://ftp.uk.debian.org) sid/main Translation-en_GB                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB      
Get: 2 [http://ftp.indexdata.dk](http://ftp.indexdata.dk) sarge Release.gpg [189B]                        
Ign [http://ftp.indexdata.dk](http://ftp.indexdata.dk) sarge/main Translation-en_GB                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg                                     
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Get: 3 [http://ftp.uk.debian.org](http://ftp.uk.debian.org) sid Release [86.5kB]                           
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Ign [http://ftp.uk.debian.org](http://ftp.uk.debian.org) sid Release                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Get: 4 [http://ftp.indexdata.dk](http://ftp.indexdata.dk) sarge Release [3454B]                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Ign [http://ftp.indexdata.dk](http://ftp.indexdata.dk) sarge Release                                      
Get: 5 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release                                         
Hit [http://ftp.uk.debian.org](http://ftp.uk.debian.org) sid/main Packages                                 
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_GB                
Get: 6 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get: 7 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get: 8 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Hit [http://ftp.indexdata.dk](http://ftp.indexdata.dk) sarge/main Packages                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages                       
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Translation-en_GB                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://ftp.indexdata.dk](http://ftp.indexdata.dk) sarge/main Sources                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages               
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                         
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release                              
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages  
Err [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages
  404 Not Found
Fetched 384B in 1s (340B/s)
W: GPG error: [http://ftp.uk.debian.org](http://ftp.uk.debian.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
W: GPG error: [http://ftp.indexdata.dk](http://ftp.indexdata.dk) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 38E53A727F1D2347
W: Failed to fetch [http://blognux.free.fr/debian/dists/unstable/main/binary-i386/Packages.gz](http://blognux.free.fr/debian/dists/unstable/main/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
------------------

I will post the upgrade when it finishes in about 2 hours.

Should one accept an upgrade when it it comes from unverified sources ?. Or just respond N and post what happened up to then ?.

Bill

---

### Post by billio on 2008-10-15
Right, did the upgrade and it screwed everything up big style: nothing worked

So, fortunately had XP on another partition and could retrieve and copy all important data.

Then obtained a new copy of Hardy Heron and reload the whole thing. A couple of days wasted but it's probably a good idea to clear out all the garbage one has built up over the months.

Thanks.

Bill

---

