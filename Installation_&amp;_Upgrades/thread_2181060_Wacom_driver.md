---
title: "Wacom driver"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by thedarkhoody on 2013-10-16
Hi, I swapped my windows 8 with ubuntu a week ago so I'm a noob. Now that I've said that, here is my problem.

I looked up in google on how to install wacom driver and tried this :

[COLOR=#444444][FONT=Consolas]sudo add-apt-repository ppa:doctormo/wacom-plus[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]sudo apt-get update[/FONT][/COLOR]
[COLOR=#444444][FONT=Consolas]sudo apt-get install wacom-dkms[/FONT][/COLOR] 

But I get an error in the third step,it says "unable to locate package wacom-dkms".

I have wacom bamboo one.


root@Sam:~# sudo add-apt-repository ppa:doctormo/wacom-plus
You are about to add the following PPA to your system:
 Wacom sometimes needs updated drivers, this is for that.
 More info: [https://launchpad.net/~doctormo/+archive/wacom-plus](https://launchpad.net/~doctormo/+archive/wacom-plus)
Press [ENTER] to continue or ctrl-c to cancel adding it
y
gpg: keyring `/tmp/tmpx3heqb/secring.gpg' created
gpg: keyring `/tmp/tmpx3heqb/pubring.gpg' created
gpg: requesting key 113659DF from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpx3heqb/trustdb.gpg: trustdb created
gpg: key 113659DF: public key "Launchpad PPA for Martin Owens" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
root@Sam:~# sudo apt-get update
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                                                                                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring Release.gpg                                                                                          
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                                              
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates Release.gpg [933 B]                                                                        
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg [933 B]                                                                              
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release.gpg                                                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                                                  
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports Release.gpg [933 B]                                          
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release [40.8 kB]                                                                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring Release                                                                            
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release                                                                                                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                                                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates Release [40.8 kB]                                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                                                                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                                                                                                
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                                                                                                                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                                                                                                     
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                                                                                                              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                                                                                                                                        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages                                                                                                                            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages                                                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                                                                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                                                                                                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                               
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages                                                                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                                                                                                                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                                                                                                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US                                                                                                            
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                                                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_GB                                                                                      
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources [46.9 kB]                                                       
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports Release [40.8 kB]                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/main Sources                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/restricted Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/universe Sources                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/multiverse Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/main amd64 Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/restricted amd64 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/universe amd64 Packages                                                                                                                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/multiverse amd64 Packages                                                                                                                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/main i386 Packages                                                                                                                                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/restricted i386 Packages                                                                                                                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/universe i386 Packages                                                                                                                                  
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources [14 B]                                                                                                                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/multiverse i386 Packages                                                                                                                                
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources [9,271 B]                                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/main Translation-en                                                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/main Translation-en_GB                                                                                                                                  
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources [2,266 B]                                                                                                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/multiverse Translation-en                                                                                                                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/multiverse Translation-en_GB                                                                                                                            
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages [122 kB]                                                                                                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/restricted Translation-en                                                                                                                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/restricted Translation-en_GB                                                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/universe Translation-en                                                                                                                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/universe Translation-en_GB                                                                                                                              
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/main Sources [75.1 kB]                                                                                                                       
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US                                                                                                                                
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                                                                                                                                         
  404  Not Found
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                                                                                                                                   
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                                                                                                                                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                                                                                                                                      
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_GB                                                                                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                                                                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_GB                                                                                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                                                                                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                                                                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_GB                                                                                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                                                                                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                                                                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_GB                                                                                                                                      
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_US                                                                                                                             
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en                                                                                                                                
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_GB                                                                                                                             
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/restricted Sources [14 B]                                                                                                                    
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/universe Sources [73.1 kB]                                                                                                                   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages [14 B]                                                                                                              
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages [38.4 kB]                                                                                                             
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages [3,715 B]                                                                                                           
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages [121 kB]                                                                                                                   
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/multiverse Sources [2,266 B]                                                                                                                 
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/main amd64 Packages [191 kB]                                                                                                                 
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages [14 B]                                                                                                               
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages [39.0 kB]                                                                                                              
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages [3,864 B]                                                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en                                                                                                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en                                                                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en                                                                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en                                                                                                                          
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/restricted amd64 Packages [14 B]                                                                                                             
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/universe amd64 Packages [150 kB]                                                                                                             
Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/multiverse amd64 Packages [3,715 B]                                                                                                          
Get:27 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/main i386 Packages [189 kB]                                                                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US                                                                                                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_GB                                                                                                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US                                                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_GB                                                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US                                                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_GB                                                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US                                                                                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_GB                                                                                                                       
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]                                                                                                              
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/universe i386 Packages [151 kB]                                                                                                              
Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/multiverse i386 Packages [3,864 B]                                                                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/main Translation-en                                                                                                                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/multiverse Translation-en                                                                                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/restricted Translation-en                                                                                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/universe Translation-en                                                                                                                         
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/main Sources [902 B]                                                                                                                       
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/restricted Sources [14 B]                                                                                                                  
Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/universe Sources [5,970 B]                                                                                                                 
Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/multiverse Sources [1,403 B]                                                                                                               
Get:35 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/main amd64 Packages [565 B]                                                                                                                
Get:36 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/restricted amd64 Packages [14 B]                                                                                                           
Get:37 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/universe amd64 Packages [6,946 B]                                                                                                          
Get:38 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/multiverse amd64 Packages [1,357 B]                                                                                                        
Get:39 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/main i386 Packages [565 B]                                                                                                                 
Get:40 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/restricted i386 Packages [14 B]                                                                                                            
Get:41 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/universe i386 Packages [6,929 B]                                                                                                           
Get:42 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/multiverse i386 Packages [1,345 B]                                                                                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/main Translation-en                                                                                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/multiverse Translation-en                                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/restricted Translation-en                                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/universe Translation-en                                                                                                                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/main Translation-en_US                                                                                                                                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/main Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/multiverse Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/restricted Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/universe Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates/universe Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/main Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/main Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/multiverse Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/multiverse Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/restricted Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/restricted Translation-en_GB
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/universe Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports/universe Translation-en_GB
Fetched 1,376 kB in 53s (25.9 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
root@Sam:~# sudo apt-get install wacom-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wacom-dkms

---

### Post by abix_adam_pl on 2013-10-16
Did you try just plug in usb cable? In My 12.04 works "out of the box" - And try to read: [SourceForge.net: Wacom Tablet Set Up - linuxwacom]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up")

Adam

---

### Post by Favux on 2013-10-16
Hi thedarkhoody,

Welcome to Ubuntu forums!


Adam's right, with Raring (13.04) you should just be able to plug in your Wacom Bamboo One tablet in and it should work.

If you want to install a PPA be sure to check the dates of the drivers.  You'll see on DoctorMo's PPA the most recent Wacom driver is from 3/11.  I'm guessing you got the instructions off the community wiki page which was last modified 6/12.  So both way out of date.  The linuxwacom wiki is likely a more up to date source:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)

---

