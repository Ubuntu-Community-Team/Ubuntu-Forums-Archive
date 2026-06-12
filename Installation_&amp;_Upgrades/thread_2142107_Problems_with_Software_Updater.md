---
title: "Problems with Software Updater"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by medphys on 2013-05-04
Hi all,

Just upgraded my system from 12.10 to 13.04 via on line about a week ago.  I usually run the software updater a few days later as in the past there are a lot of updates.  When I try the software updater I get the following: FAILED TO DOWNLOAD THE REPOSITORY INFORMATION check your internet connection.  My connection is fine no problems.  

1.  Has anyone else experienced this with the software updater?
2.  How do I fix it?

Thanks for the help.

---

### Post by MAFoElffen on 2013-05-04
First try 
```

ping -c 5 http://us.archive.ubuntu.com/ubuntu/dists/raring/main/ && traceroute www.ubuntu.com

```
Or substitute for the archive server you are using if not in the US... Look in /etc/apt/sources.list to see which archive you are using.

Please post the results.

---

### Post by ibjsb4 on 2013-05-05
Also try updating in terminal to see what errors you get.

```
sudo apt-get update
```

---

### Post by medphys on 2013-05-05
Hi  ibjsb4,

Thanks for your help.  Here are the results pf the ping and the sudo apt-get update.  Hope this helps.

$ ping -c 5 [http://us.archive.ubuntu.com/ubuntu/dists/raring/main/](http://us.archive.ubuntu.com/ubuntu/dists/raring/main/) && traceroute [www.ubuntu.com](www.ubuntu.com)
ping: unknown host [http://us.archive.ubuntu.com/ubuntu/dists/raring/main/](http://us.archive.ubuntu.com/ubuntu/dists/raring/main/)

Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports Release.gpg                   
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports Release                       
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main i386 Packages            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted i386 Packages      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release.gpg                           
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe i386 Packages        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse i386 Packages      
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg                       
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security Release.gpg                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages                        
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe i386 Packages                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse i386 Packages                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main Translation-en_US        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free i386 Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main Translation-en           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse Translation-en_US  
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse Translation-en     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted Translation-en     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe Translation-en       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe i386 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Translation-en        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages               
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Translation-en        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
  404  Not Found
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en_US                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Translation-en          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/free Translation-en                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
  404  Not Found
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) raring/non-free Translation-en               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-security/universe Translation-en_US
W: Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Also checked the server, using us server.  Switched servers and used main server and results are the same.

Thank you again for your help.

medphys

---

### Post by ibjsb4 on 2013-05-05
All those launchpad ppa's do not have a source for your current version (raring) and need to be either removed or just unchecked for now.  Maybe down the road these ppa's will get updated, but for now they will just mess up your updates.

[http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/)
[http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/)
[http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/)
[http://ppa.launchpad.net/](http://ppa.launchpad.net/)

Open up "other software" in your Software Sources to edit.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

---

### Post by medphys on 2013-05-05
Thanks,

Unchecked them all and it worked.  Never thought that was the problem.

---

### Post by ibjsb4 on 2013-05-05
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

