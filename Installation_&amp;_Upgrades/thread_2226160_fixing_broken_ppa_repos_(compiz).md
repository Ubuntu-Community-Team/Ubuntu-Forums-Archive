---
title: "fixing broken ppa repos (compiz)"
date: 2014-05-25
forum: Installation &amp; Upgrades
---

### Post by Drone4four on 2014-05-25
I found an answer a question about how to install boot-repair on 14.04 with a ppa that hasn't been updated for trusty.  This was the solution:

```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list"
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

```

It worked like a charm.  So I did my best to adapt that solution to install compiz 0.8.8 with packages that were compiled for raring.  compiz 0.8.8 hasn't changed in years, so I figured this would be OK to try.  I entered these commands:

```
sudo add-apt-repository ppa:niclasoverby/compiz-0.8.8
sudo sh -c "sed -i 's/trusty/raring/g' /etc/apt/sources.list.d/niclasoverby-compiz-0_8_8-trusty.list"
sudo apt-get update

```

Rather than installing compiz in my shell, I thought I'd use synaptic to verify the existence of packages for compiz 0.8.8.  All I found was 0.9.x.  

So I decided to remove the nicholas' ppa.

I enter this command:

```

**~ $** sudo add-apt-repository --remove ppa:niclasoverby/compiz-0.8.8 

```

Now I get this when running apt-get update:

```

**~ $** sudo apt-get update
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed InRelease                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Ign [http://packages.bodhilinux.com](http://packages.bodhilinux.com) trusty InRelease                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release.gpg                   
Get:1 [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release.gpg [489 B]                      
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty InRelease                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Ign [http://packages.bodhilinux.com](http://packages.bodhilinux.com) trusty Release.gpg                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release                        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release [2,601 B]                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://packages.bodhilinux.com](http://packages.bodhilinux.com) trusty Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty Release.gpg                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages                  
Ign [http://packages.bodhilinux.com](http://packages.bodhilinux.com) trusty/main amd64 Packages/DiffIndex        
Get:3 [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main amd64 Packages [1,143 B]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://packages.bodhilinux.com](http://packages.bodhilinux.com) trusty/main i386 Packages/DiffIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                   
Get:4 [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main i386 Packages [1,143 B]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty/main amd64 Packages/DiffIndex          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty/main i386 Packages/DiffIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty/main amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages             
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://packages.bodhilinux.com](http://packages.bodhilinux.com) trusty/main amd64 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://packages.bodhilinux.com](http://packages.bodhilinux.com) trusty/main i386 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Ign [http://packages.bodhilinux.com](http://packages.bodhilinux.com) trusty/main Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Ign [http://packages.bodhilinux.com](http://packages.bodhilinux.com) trusty/main Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages              
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty/main Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main amd64 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse i386 Packages
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted i386 Packages
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-proposed/universe Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                         
Fetched 5,376 B in 8s (631 B/s)                                                
Reading package lists... Done
[COLOR="#FF0000"]W: Duplicate sources.list entry [http://ppa.launchpad.net/niclasoverby/compiz-0.8.8/ubuntu/](http://ppa.launchpad.net/niclasoverby/compiz-0.8.8/ubuntu/) raring/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_niclasoverby_compiz-0.8.8_ubuntu_dists_raring_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/niclasoverby/compiz-0.8.8/ubuntu/](http://ppa.launchpad.net/niclasoverby/compiz-0.8.8/ubuntu/) raring/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_niclasoverby_compiz-0.8.8_ubuntu_dists_raring_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems[/COLOR]
**~ $** 
```

Notice the code in red font? I did run sudo apt-get update, but it didn't correct these problems.

```

**/etc/apt/sources.list.d $ **ls
dropbox.list
dropbox.list.save
fossfreedom-packagefixes-trusty.list
fossfreedom-packagefixes-trusty.list.save
gnome3-team-gnome3-staging-trusty.list
gnome3-team-gnome3-staging-trusty.list.save
google-chrome.list
google-chrome.list.save
google-webdesigner.list
google-webdesigner.list.save
hannes-janetzek-enlightenment-svn-trusty.list
hannes-janetzek-enlightenment-svn-trusty.list.save
niclasoverby-compiz-0_8_8-trusty.list
niclasoverby-compiz-0_8_8-trusty.list.save
ricotz-testing-trusty.list
ricotz-testing-trusty.list.save
steam.list
steam.list.save
tualatrix-ppa-trusty.list
tualatrix-ppa-trusty.list.save
vase-ppa-trusty.list
vase-ppa-trusty.list.save
yannubuntu-boot-repair-trusty.list
yannubuntu-boot-repair-trusty.list.save
**/etc/apt/sources.list.d $**

```
nicholas' ppas still exists in my sources.list.d, along with hannes' and ricotz'.  I thought I removed them a few days ago, but apparently they still exist too. How do I remove them?

---

### Post by Drone4four on 2014-05-25
Yikes! After spending the better part of half an hour assembling the above post, an answer came to me: I just renamed the two nicholas files by appending .bak to them.  sudo apt-get update then completes without returning the &#8220;Duplicate...&#8221; error.  

Before I mark this thread as solved, I'd like to know if my 'fix' is safe for my package-manager? Am I setting myself up for breaking packages in the future somehow?

---

### Post by egeezer on 2014-06-02
Any results to report? I don't mean to intrude, but I sent you a PM with a more detailed question.

---

### Post by Bucky Ball on 2014-06-02
I usually just go to the Update Manager>Settings>Other Software and either untick or remove the unwanted PPAs ...

---

