---
title: "Upgrade Problem to 16.04 from 14.04 - &quot;Failed to download repository information chec"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by niceguy123 on 2016-04-22
What is the easiest way to launch an upgrade from 14.04 to 16.04. I think I remember in the past getting a pop up notice to click and approve the update. I haven't seen that after last upgrading to 14.04. 

Thanks,

---

### Post by howefield on 2016-04-22
I don't believe you will be notified of an upgrade going from 14.04 to 16.04 till the first point release, ie 16.04.1

From the download page..

> Upgrading from Ubuntu 14.04 LTS or 15.10
14.04 LTS to LTS upgrades will be enabled with the 16.04.1 LTS point release, in approximately 3 months time.

To upgrade on a desktop system:

Open the "Software & Updates" Setting in System Settings.
Select the 3rd Tab called "Updates".
Set the "Notify me of a new Ubuntu version" dropdown menu to "For any new version" if you are using 15.10, set it to "long-term support versions" if you are using 14.04 LTS.
Press Alt+F2 and type in "update-manager" (without the quotes) into the command box.
Software Updater should open up and tell you: New distribution release '16.04 LTS' is available.
Click Upgrade and follow the on-screen instructions.
To upgrade on a server system:

Install the update-manager-core package if it is not already installed.
Make sure the /etc/update-manager/release-upgrades is set to normal if you are using 15.10, lts if you are using 14.04 LTS.
Launch the upgrade tool with the command sudo do-release-upgrade.
Follow the on-screen instructions.
Note that the server upgrade will use GNU screen and automatically re-attach in case of dropped connection problems.

---

### Post by niceguy123 on 2016-04-22
after I do: Press Alt+F2 and type in "update-manager" (without the quotes) into the command box.

I get a pop up that says "Failed to download repository information check your internet connection"

I am connected to the internet and browsing other sites with no problem.

 [IMG]https://goo.gl/photos/ykpSPbknZDG2eSao8[/IMG]

---

### Post by niceguy123 on 2016-07-04
Hi this is the notice that I am getting. Something is wrong with my repository settings and I can't get an upgrade. How can I fix this?

[IMG]https://lh3.googleusercontent.com/SeWT7C9e8syqGKxIc4fCa1PH4yvPmYaM4U7pc_JCu6G8LLM36iQ9i9hfTfWJ5wZLtr-h39PTDXg8LfHfG0BkNmdQJxaz502utwotDHddb6C_mxUEX3W-Fz6O_Ty5W9x_LxmJT3EJ0yGLaaoHWzycILP8eznZQKqieSa-ThYDywEyoQqimaXWwohJow68aET5JhY2SiRE_c3deF4LT8otO_x7qwY3MUn2sNL0a-wqkm1rudB5A02qBHxQDK4E7GVhMV1eVYfM3oVwEkEyW2rRfxnTG1uCiUKz9L1sku7KO-NJlD1wAOyPLDdCDJ4lxSu4D6JYRBpO9sXiM-fV90Ijft3yu0LRrKWaS3eXWW1vJHro3VMiwxCQy87UvMQViIr-BTOxPdafSI2V6vNmkTQ7-d8IduHpAx-vIMBwpbV-bOAbFbRhhXe7JRlDOPj6LWgyR9tUNZ0X0qkL_E-e16Qy2-8f1eMIXK-Vr2qfgKq6P2TC55WACQqAQ2sZ0lR3Z6SY-KNGnzcLprZz6RYEqFsMfg6c2C1hUSLnNT5i2m_1y-2gwx4B9U6r4KIAxCwD7KGnNPXlNr4N7J2YnLntOMdItYWeKZNFnZqI=w486-h145-no[/IMG]

---

### Post by kansasnoob on 2016-07-04
Please open a terminal, run the following command, and then copy-n-paste that full terminal output here so we can see what may be going on:

```
sudo apt-get update
```

---

### Post by niceguy123 on 2016-07-04
```
vfav@Dell:~$ sudo apt-get update
[sudo] password for agag: 
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring InRelease
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring Release.gpg
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring Release
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main Translation-en_US
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main Translation-en
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main Translation-en_AU
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted Translation-en_US
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted Translation-en
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted Translation-en_AU
Hit http://archive.canonical.com raring InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://dl.google.com stable InRelease                                      
Get:1 http://deb.opera.com stable InRelease [2,592 B]                          
Ign http://dl.google.com stable InRelease                                      
Get:2 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Hit http://dl.google.com stable Release.gpg                                    
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://deb.opera.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Get:3 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://archive.canonical.com raring/partner Sources                        
Ign http://deb.opera.com stable/non-free amd64 Packages/DiffIndex              
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://dl.google.com stable Release                                        
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://dl.google.com stable Release                                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://www.openprinting.org lsb3.2 InRelease                               
Hit https://private-ppa.launchpad.net trusty Release                           
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://www.openprinting.org lsb3.2 Release.gpg                             
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Hit http://us.archive.ubuntu.com trusty-security InRelease                     
Hit http://www.openprinting.org lsb3.2 Release                                 
Get:4 http://us.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]         
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                  
Get:5 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,936 B] 
Get:6 http://us.archive.ubuntu.com trusty-updates/main Sources [277 kB]        
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                   
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en_AU                     
Get:7 http://us.archive.ubuntu.com trusty-updates/universe Sources [158 kB]    
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted Sources [5,352 B] 
Ign https://private-ppa.launchpad.net trusty/main Translation-en_AU            
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Get:9 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [789 kB] 
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Ign http://deb.opera.com stable/non-free Translation-en_AU                     
Get:10 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:11 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [363 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Get:13 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [756 kB] 
Get:14 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:15 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [364 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US               
Get:17 http://us.archive.ubuntu.com trusty-updates/main Translation-en [396 kB]
Hit http://www.openprinting.org lsb3.2/contrib Translation-en                  
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_AU               
Get:18 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,227 B]
Get:19 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:20 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [191 kB]
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty-security/multiverse Sources            
Hit http://us.archive.ubuntu.com trusty-security/main Sources                  
Hit http://us.archive.ubuntu.com trusty-security/universe Sources              
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com trusty-security/restricted Sources            
Hit http://us.archive.ubuntu.com trusty-security/main amd64 Packages           
Hit http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com trusty-security/universe amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com trusty-security/main i386 Packages            
Hit http://us.archive.ubuntu.com trusty-security/restricted i386 Packages      
Hit http://us.archive.ubuntu.com trusty-security/universe i386 Packages        
Hit http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Ign http://dl.google.com stable/main Translation-en_AU                         
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_AU                         
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Get:21 http://us.archive.ubuntu.com trusty-proposed/multiverse amd64 Packages [28 B]
Get:22 http://us.archive.ubuntu.com trusty-proposed/main amd64 Packages [139 kB]
Get:23 http://us.archive.ubuntu.com trusty-proposed/universe amd64 Packages [21.1 kB]
Get:24 http://us.archive.ubuntu.com trusty-proposed/restricted amd64 Packages [28 B]
Get:25 http://us.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:26 http://us.archive.ubuntu.com trusty-proposed/main i386 Packages [134 kB]
Get:27 http://us.archive.ubuntu.com trusty-proposed/universe i386 Packages [21.1 kB]
Get:28 http://us.archive.ubuntu.com trusty-proposed/restricted i386 Packages [28 B]
Get:29 http://us.archive.ubuntu.com trusty-proposed/main Translation-en [54.0 kB]
Get:30 http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en [28 B]
Get:31 http://us.archive.ubuntu.com trusty-proposed/restricted Translation-en [28 B]
Get:32 http://us.archive.ubuntu.com trusty-proposed/universe Translation-en [19.2 kB]
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Get:33 http://us.archive.ubuntu.com trusty/main Translation-en_AU [2,649 B]    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Get:34 http://us.archive.ubuntu.com trusty/multiverse Translation-en_AU [75.6 kB]
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Get:35 http://us.archive.ubuntu.com trusty/restricted Translation-en_AU [2,668 B]
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:36 http://us.archive.ubuntu.com trusty/universe Translation-en_AU [3,469 kB]
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 7,446 kB in 25s (297 kB/s)                                             
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
hadsf@Dell:~$
```

---

### Post by kansasnoob on 2016-07-04
It's looking for some old Raring repos. Maybe you had a Raring DVD/USB inserted sometime and enabled it? These screenshots are from Xenial but if you open the Software and Updates UI look for Raring CD being enabled in one of these two places:

[ATTACH=CONFIG]269957[/ATTACH]

[ATTACH=CONFIG]269958[/ATTACH]

If you see the Raring source listed in either of those places disable it and try again:

```
sudo apt-get update
```

There may be other errors also but we'll work one step at a time.

---

### Post by niceguy123 on 2016-07-05
Ok, I found Raring repos here and unchecked it and then ran sudo apt-get update see below some errors that came up.

 [IMG]https://lh3.googleusercontent.com/CNbwOJKhPa_sMe2msnRWc24F1O2FiYbAy_ZbgnMUXxQcQ_XgbsgfqYguFds4fOj631NoFiKjZXQQT63bIq1vRGfzVijFS1xN7q8IjdYvLSn9_QTFyZe-ClC1_8AZkKuWwfuXZQxTWciLyr8LYrv5pzCyUU8ASPUVIoWEFJnE66W4aeweIsq80PM4X42uH5AOivK7htUL1fiMmMLSgJImzWe0m1l8mQIvmz5xkMxYuaNzkZV6J1uvAbA8pGwx0ZEUi1Ho2rEZT_jOxicpjT9OeJSZI3K5VikqXKRNQFf0foRPOzlTktk8hLATMkL-IBXH4FJvSLF-xF-ZGrAjKYt65D1qi3lzxpEV7zRAf3--1i3_MreJ2FuDw1_LF3cXLzhswxS13zxKGL3WL-qAEkYnjXJ712VHcIRdfVdADoJyvEQ3h_Zw8Vyrm9JfNe-_iZTCWq7NE7eSmDZUUXGGG_8Y0idGN6B86pkbmjGZEvwDSZal7wumuByZhwCmXgyRk0xAJSONaEgeeFv82b5yambxEyfNlj1VMJthWWNXEek6MUSZp84gixOQ-DhcgQ03me2GYMq8agDTey-ucpfzeg-8kv2_LQ_eJ0l5=w1169-h641-no[/IMG]

```
****@Dell:~$ sudo apt-get update
[sudo] password for ****: 
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring InRelease
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring Release.gpg
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring Release
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main Translation-en_US
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main Translation-en
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/main Translation-en_AU
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted Translation-en_US
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted Translation-en
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424) raring/restricted Translation-en_AU
Hit http://archive.canonical.com raring InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://dl.google.com stable InRelease                                      
Get:1 http://deb.opera.com stable InRelease [2,592 B]                          
Ign http://dl.google.com stable InRelease                                      
Get:2 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Hit http://dl.google.com stable Release.gpg                                    
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://deb.opera.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Get:3 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://archive.canonical.com raring/partner Sources                        
Ign http://deb.opera.com stable/non-free amd64 Packages/DiffIndex              
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://dl.google.com stable Release                                        
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://dl.google.com stable Release                                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://www.openprinting.org lsb3.2 InRelease                               
Hit https://private-ppa.launchpad.net trusty Release                           
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://www.openprinting.org lsb3.2 Release.gpg                             
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Hit http://us.archive.ubuntu.com trusty-security InRelease                     
Hit http://www.openprinting.org lsb3.2 Release                                 
Get:4 http://us.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]         
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                  
Get:5 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,936 B] 
Get:6 http://us.archive.ubuntu.com trusty-updates/main Sources [277 kB]        
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                   
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en_AU                     
Get:7 http://us.archive.ubuntu.com trusty-updates/universe Sources [158 kB]    
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted Sources [5,352 B] 
Ign https://private-ppa.launchpad.net trusty/main Translation-en_AU            
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Get:9 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [789 kB] 
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Ign http://deb.opera.com stable/non-free Translation-en_AU                     
Get:10 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:11 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [363 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Get:13 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [756 kB] 
Get:14 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:15 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [364 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US               
Get:17 http://us.archive.ubuntu.com trusty-updates/main Translation-en [396 kB]
Hit http://www.openprinting.org lsb3.2/contrib Translation-en                  
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_AU               
Get:18 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,227 B]
Get:19 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:20 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [191 kB]
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty-security/multiverse Sources            
Hit http://us.archive.ubuntu.com trusty-security/main Sources                  
Hit http://us.archive.ubuntu.com trusty-security/universe Sources              
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com trusty-security/restricted Sources            
Hit http://us.archive.ubuntu.com trusty-security/main amd64 Packages           
Hit http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com trusty-security/universe amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com trusty-security/main i386 Packages            
Hit http://us.archive.ubuntu.com trusty-security/restricted i386 Packages      
Hit http://us.archive.ubuntu.com trusty-security/universe i386 Packages        
Hit http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Ign http://dl.google.com stable/main Translation-en_AU                         
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_AU                         
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Get:21 http://us.archive.ubuntu.com trusty-proposed/multiverse amd64 Packages [28 B]
Get:22 http://us.archive.ubuntu.com trusty-proposed/main amd64 Packages [139 kB]
Get:23 http://us.archive.ubuntu.com trusty-proposed/universe amd64 Packages [21.1 kB]
Get:24 http://us.archive.ubuntu.com trusty-proposed/restricted amd64 Packages [28 B]
Get:25 http://us.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:26 http://us.archive.ubuntu.com trusty-proposed/main i386 Packages [134 kB]
Get:27 http://us.archive.ubuntu.com trusty-proposed/universe i386 Packages [21.1 kB]
Get:28 http://us.archive.ubuntu.com trusty-proposed/restricted i386 Packages [28 B]
Get:29 http://us.archive.ubuntu.com trusty-proposed/main Translation-en [54.0 kB]
Get:30 http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en [28 B]
Get:31 http://us.archive.ubuntu.com trusty-proposed/restricted Translation-en [28 B]
Get:32 http://us.archive.ubuntu.com trusty-proposed/universe Translation-en [19.2 kB]
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Get:33 http://us.archive.ubuntu.com trusty/main Translation-en_AU [2,649 B]    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Get:34 http://us.archive.ubuntu.com trusty/multiverse Translation-en_AU [75.6 kB]
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Get:35 http://us.archive.ubuntu.com trusty/restricted Translation-en_AU [2,668 B]
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:36 http://us.archive.ubuntu.com trusty/universe Translation-en_AU [3,469 kB]
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 7,446 kB in 25s (297 kB/s)                                             
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
haivri@Dell:~$ ^C
haivri@Dell:~$ sudo apt-get update
[sudo] password for haivri: 
Ign http://extras.ubuntu.com trusty InRelease
Ign http://dl.google.com stable InRelease                                      
Get:1 http://deb.opera.com stable InRelease [2,592 B]                          
Ign http://deb.opera.com stable InRelease                                      
Get:2 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Ign http://dl.google.com stable InRelease                                      
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://deb.opera.com stable/non-free amd64 Packages/DiffIndex              
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.canonical.com raring InRelease                              
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:3 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://archive.canonical.com raring/partner Sources                        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:4 http://archive.canonical.com raring/partner amd64 Packages [3,105 B]     
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:5 http://archive.canonical.com raring/partner i386 Packages [3,808 B]      
Ign https://private-ppa.launchpad.net trusty InRelease                         
Ign http://www.openprinting.org lsb3.2 InRelease                               
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Hit https://private-ppa.launchpad.net trusty Release                           
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://www.openprinting.org lsb3.2 Release.gpg                             
Hit http://us.archive.ubuntu.com trusty-security InRelease                     
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Hit http://www.openprinting.org lsb3.2 Release                                 
Get:6 http://us.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]         
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                  
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Get:7 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [789 kB] 
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                   
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en_AU                     
Hit http://dl.google.com stable Release.gpg                                    
Ign http://archive.canonical.com raring/partner Translation-en_US              
Hit http://dl.google.com stable Release                                        
Ign http://archive.canonical.com raring/partner Translation-en                 
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://archive.canonical.com raring/partner Translation-en_AU              
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Ign http://deb.opera.com stable/non-free Translation-en_AU                     
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Get:9 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [363 kB]
Ign https://private-ppa.launchpad.net trusty/main Translation-en      
Ign https://private-ppa.launchpad.net trusty/main Translation-en_AU            
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:11 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [756 kB] 
Get:12 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US               
Get:13 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [364 kB]
Hit http://www.openprinting.org lsb3.2/contrib Translation-en                  
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_AU               
Get:15 http://us.archive.ubuntu.com trusty-updates/main Translation-en [396 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,227 B]
Get:17 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:18 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [191 kB]
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty-security/main amd64 Packages           
Hit http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com trusty-security/universe amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com trusty-security/main i386 Packages            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty-security/restricted i386 Packages      
Ign http://dl.google.com stable/main Translation-en_AU                         
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com trusty-security/universe i386 Packages        
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages      
Ign http://dl.google.com stable/main Translation-en_AU                         
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Get:19 http://us.archive.ubuntu.com trusty-proposed/multiverse amd64 Packages [28 B]
Get:20 http://us.archive.ubuntu.com trusty-proposed/main amd64 Packages [139 kB]
Get:21 http://us.archive.ubuntu.com trusty-proposed/universe amd64 Packages [21.1 kB]
Get:22 http://us.archive.ubuntu.com trusty-proposed/restricted amd64 Packages [28 B]
Get:23 http://us.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:24 http://us.archive.ubuntu.com trusty-proposed/main i386 Packages [134 kB]
Get:25 http://us.archive.ubuntu.com trusty-proposed/universe i386 Packages [21.1 kB]
Get:26 http://us.archive.ubuntu.com trusty-proposed/restricted i386 Packages [28 B]
Hit http://us.archive.ubuntu.com trusty-proposed/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-proposed/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-proposed/universe Translation-en       
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/main Translation-en_AU                 
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en_AU           
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en_AU           
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Hit http://us.archive.ubuntu.com trusty/universe Translation-en_AU             
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 3,384 kB in 23s (145 kB/s)                                             
Reading package lists... Done
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
****@Dell:~$ 

```

---

### Post by kansasnoob on 2016-07-05
Is it also enabled under the Ubuntu Software tab clear at the bottom as in my first screenshot?

It's still looking for Raring sources. If all else fails we may have to look at:

```
cat /etc/apt/sources.list
```

And:

```
ls /etc/apt/sources.list.d
```

---

### Post by niceguy123 on 2016-07-05
Here is the screen shot for software and updates. (See below readout for two comands).

[IMG]https://lh3.googleusercontent.com/38yxzoZcKVkiuX1KRCAr48oNBn2w36nFPq8WiWPBpqrxE-RZh7CpcRvBO5ArdFAcrz7feub4r9h5Dc1WscZ_djxd5sZ5C4UwGrwUZmBIVi5YN-kjEduooPTIh2s7QP4AI9QMab0bVak0k0M9LIsn7L15gOiyxGiwm_6kHUOCKw11oh8Qcc9b7fJNBEL_S7UiXAc4pUVNvus1OOxbKn68lj28aUs1_qtPGjQibs2uS533i7XyEHTHL2f1D88Ob9ShJBERSUJ3MUP-_wM8UZCIE0e2PY4lUx4HOFIv8h5d7RtPGkMiN1UfsaYr0L-NsQx75yMlod9DnElau1SdvEtpZizel2tiNgzZDy1ZUr38HD0I1M-wBEIhnJ51TBnbg0S8lgw4EKlIJNMWrxLR3nlS2_VuSVMIO4PHIKxBQnhKeG6zsCfP5t09htGLFjtFai-MaNc8fLJw29ri8o1hkXru7h562dMay9Uc_bwIWZIWpQyvSD74Ff-WYNY5K9DLngPMM2vGM7hI7QmnlaP7UrGR5EQ3yC1diwo5tBCEFl7dXW6U7Kop42wZMz59_Ymraxo8zXik1HL0TBUI2Gi2jOWcdPedHqAFPXgh=w604-h470-no[/IMG]


```
@Dell:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib
deb http://us.archive.ubuntu.com/ubuntu/ trusty-proposed multiverse main universe restricted

```

```
@Dell:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib
deb http://us.archive.ubuntu.com/ubuntu/ trusty-proposed multiverse main universe restricted
haivri@Dell:~$ ls /etc/apt/sources.list.d
google-chrome.list	     opera.list.save
google-chrome.list.save      private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list
google-talkplugin.list	     private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.distUpgrade
google-talkplugin.list.save  private-ppa.launchpad.net_commercial-ppa-uploaders_master-pdf-editor_ubuntu.list.save
opera.list		     private-ppa.launchpad.net_commercial-ppa-uploaders_slimboat_ubuntu.list
opera.list.distUpgrade	     private-ppa.launchpad.net_commercial-ppa-uploaders_slimboat_ubuntu.list.save
```

---

### Post by geogur on 2016-07-05
i bought the usb and crashed on install loosing ringtail not getting 16.04 lts 
(backed up) now im in no mans land only exist live on usb and cant install

my point is i too fail to get the repository somethingy and it crashes 
i did the down loads for 3 weeks before i sent away for the usb that dosnt work

---

### Post by niceguy123 on 2016-07-06
@geogur, 

Thanks for sharing, though that is not encouraging.

---

### Post by kansasnoob on 2016-07-06
I highlighted the offending lines in red:

```
@Dell:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
[B][COLOR="#FF0000"]deb http://archive.canonical.com/ubuntu raring partner
deb-src http://archive.canonical.com/ubuntu raring partner[/COLOR][/B]

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib
deb http://us.archive.ubuntu.com/ubuntu/ trusty-proposed multiverse main universe restricted


```

I don't want you to just remove those lines entirely because I'm not sure if that last line about trusty-proposed is right or not!

So please comment those lines out using ##. You would want to run:

```
sudo gedit /etc/apt/sources.list
```

Then add the ## shown here in red:

```
@Dell:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
**[COLOR="#FF0000"]##[/COLOR]**deb http://archive.canonical.com/ubuntu raring partner
[COLOR="#FF0000"]##[/COLOR]deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib
deb http://us.archive.ubuntu.com/ubuntu/ trusty-proposed multiverse main universe restricted


```

Then click on Save in gedit before closing and once again try:

```
sudo apt-get update
```

Then we'll see if there are additional errors :)

---

### Post by niceguy123 on 2016-07-07
Some updates on this situation:

Something related to the above suggestions must had helped. Today when I turned on my computer the automatic update alert notified me that my ubuntu 14.04 is out of date and that I can choose to update to 15.04. I chose that option and it started to install. But then the installation stopped and I got this error message:

[IMG]https://lh3.googleusercontent.com/KE-0oIl_sflvgu7WcTUnF6CIb547hjEuKEpq0QYK6f4Y5zC0wdur9xlv4vAqCuAugsAR1qNZqyJCaWzJ2JRdhtESHjnhL8iYYsX15rVC0tjjCroxqLNFi7IBBh8hiJEu-PjKrCcmgDiSrkuk5P2DEwL1HqgJwrKIvnagV2LcE4GHMpGa_qT_zW62PHOf9KwBiIOPWJSeA-5iLK09NxXI6yvtHSRVomREe1ZX_Dtq4ZB4NjoYpOqWkn1ERVlCxEjelHRQ7zEnF1CUWXgzIDaUwYXdxFAB7L1dN6cd7_rr9kJkWacFCGuhzC4krmLihzhRXHtpE8_eHUBH3ibNtEyak1K_MSpgYi9iXA0xq9SkFEPGlHBx0Ai93beqxXmgr_Azhtr8P-U1rfxcbRsQrSiFCtArBA_LUdm4CMAkLRR86OvjJxxK4BX4jXQ8UXg_2twAP2dOUzrbK6VPRR8lRHU7_z7qh5zIyUsjfWxIr3hPvmu591Rbzi_84kfP-Y1V5BamYa9LGNsK5dZExQ3N1MdimJI_esPWZnPrDYOx4tPwCac112gbYroQfBNkJtGedR5Pbt9YZ3eHGxsTKcRxabYJIDE_oZHfCmLu=w671-h641-no[/IMG]

I ran apt-get in terminal and this is what I got:

```
@Dell:~$ apt-get
apt 1.0.1ubuntu2 for amd64 compiled on May 18 2016 09:49:01
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.

```

---

### Post by kansasnoob on 2016-07-07
> **niceguy123 said:**
> Some updates on this situation:

Something related to the above suggestions must had helped. Today when I turned on my computer the automatic update alert notified me that my ubuntu 14.04 is out of date and that I can choose to update to 15.04. I chose that option and it started to install. But then the installation stopped and I got this error message:

[IMG]https://lh3.googleusercontent.com/KE-0oIl_sflvgu7WcTUnF6CIb547hjEuKEpq0QYK6f4Y5zC0wdur9xlv4vAqCuAugsAR1qNZqyJCaWzJ2JRdhtESHjnhL8iYYsX15rVC0tjjCroxqLNFi7IBBh8hiJEu-PjKrCcmgDiSrkuk5P2DEwL1HqgJwrKIvnagV2LcE4GHMpGa_qT_zW62PHOf9KwBiIOPWJSeA-5iLK09NxXI6yvtHSRVomREe1ZX_Dtq4ZB4NjoYpOqWkn1ERVlCxEjelHRQ7zEnF1CUWXgzIDaUwYXdxFAB7L1dN6cd7_rr9kJkWacFCGuhzC4krmLihzhRXHtpE8_eHUBH3ibNtEyak1K_MSpgYi9iXA0xq9SkFEPGlHBx0Ai93beqxXmgr_Azhtr8P-U1rfxcbRsQrSiFCtArBA_LUdm4CMAkLRR86OvjJxxK4BX4jXQ8UXg_2twAP2dOUzrbK6VPRR8lRHU7_z7qh5zIyUsjfWxIr3hPvmu591Rbzi_84kfP-Y1V5BamYa9LGNsK5dZExQ3N1MdimJI_esPWZnPrDYOx4tPwCac112gbYroQfBNkJtGedR5Pbt9YZ3eHGxsTKcRxabYJIDE_oZHfCmLu=w671-h641-no[/IMG]

I ran apt-get in terminal and this is what I got:

```
@Dell:~$ apt-get
apt 1.0.1ubuntu2 for amd64 compiled on May 18 2016 09:49:01
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.

```

That will likely result in even further breakage :(

Now we need to start all over because the upgrade process may have changed the software sources.

I assume you must have changed Notify me of a new version from LTS only to any new version. This could be quite bad. At the very least you'd have to upgrade again very soon.

---

### Post by niceguy123 on 2016-07-07
> **kansasnoob said:**
> That will likely result in even further breakage :(

Now we need to start all over because the upgrade process may have changed the software sources.

I assume you must have changed Notify me of a new version from LTS only to any new version. This could be quite bad. At the very least you'd have to upgrade again very soon.

Not sure what you mean and what I should do. 

[IMG]https://lh3.googleusercontent.com/iSs4t1ReGTbPFXGqF_GspiZrWLMm4tpwB-himYRdUAU83F1tnJCklsIJhBev5dEP-APNoC1hCtuSO76HsMmtfyMyb05DZOJOuZcIvg8pKfPVTl8JPXswtm3kBZk4AbvLGjrtwc5kPwFTXIgkkTamx-DIBq857ZbHUeH6ZdV_2mfanMlIupQJJ2_V-6IMUvZ_SPb--gi2LPQNky4XPgGGakSRJ2rPWH9eE7ZG8mbKdSd0DPTy8bAu0q0gzxLonzckFivWeFaAxFu-GpLdAhpw7YrgIDJJlRIWud3qPi24M8TLSRhgcC6Cg-GDas_lHRbQA1gKJ8enEn0k2T2HsDjM_2pIKW_olP41V1g068c-kdItmq81YZnsh2WHMvEss4pNdmgDfQDgoXbfoiZjJOo_kIYhrAbW9PYPVd3MrfM1s11iBaj-3XlARZW7uP_SE8Wl2uoa-OUS0HLMSdhKefTIMeoLT-P-Q1z0ExvCEjqbRlf5JGlPbOTVXn_GTu9FKjJ2GXK6h3TB_0pUEYjZvAXkQqDhFPWAsfA3UDsV7rW6cPPCdA0o8ZLFhefZgnJIXhO4Bm7HrRSEiJd-bqUZx50P5xccU68l_v7T=w603-h469-no[/IMG]

---

### Post by kansasnoob on 2016-07-07
We need to see your software sources again to see if the failed upgrade process changed anything:

```
cat /etc/apt/sources.list
```

Also, open the Software & Updates UI again and under the Updates tab look at the very bottom where it says "Notify me of a new Ubuntu version". Make sure it's set to "For long term supported versions only". We can discuss that later, but it's pointless to even think about upgrading to a new version while things are broken.

---

### Post by kansasnoob on 2016-07-07
BTW please don't apply any updates until we get this straightened out! I assume you can still boot the OS :confused:

---

### Post by niceguy123 on 2016-07-07
```
@Dell:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib
deb http://us.archive.ubuntu.com/ubuntu/ trusty-proposed multiverse main universe restricted

```

Here I changed settings for updates. 
[IMG]https://lh3.googleusercontent.com/JT2lIe5m0pT19UIj1mnTVDe8jpeC3CxBE6MSbJQrxiehFWYiZ_Ek9Digmsfbb4PrlDOy71gJajtRMXK53QQq2dtsTta4Q0iGATKfM92CUyKRvUKlwGyZ-qqAn8Oe5FSU0RyAq5N5MH-v5Ec2yX1LYFPWWYW7jjRVUxNsoOZU3KNVBsux-aTliPVbeIreQU_aQf9ma9DIdmkXyDBsODFw_ECS3AWkHExIidi8AeZq6ErflfKXlq042mo0JMgU7JGj0neYZFJtF5Vn4l2YtifuHxEQrImKMbZM92iiAe1yKKIp8gn6iMAeq_uy0jlmpXeiiYqUNJQYEV_w92DEiQ7bMxZYWfbBIqpkoMpjhnMrtgsXOtQc-9kXR7oQIBRa-MIGy4G7rIxvuUtfLvWYz0Tt81UASV_v98_CMy9ExmCbsV3jsiHqxVUI7ZTm2RVticDSuKaatqdmAEYbhTOnUyZAC8TgByXf9Lnxhl6tv-qVZ-uvk9QqFGxy4zOCD3bYmx5CU_zMcLGhFm5ZHhtSc1QIHT9ZZ49ZzuN7hQnKtPbBuOtoEyOEfwxgVcbOE3hZV58fogfS3ghn2CKKl6kxj7dK4u12TwkiT8p6=w602-h470-no[/IMG]

---

### Post by kansasnoob on 2016-07-07
Good, we're still on Trusty. So comment out the Raring lines as I showed in comment #13:

[http://ubuntuforums.org/showthread.php?t=2321328&page=2&p=13514377#post13514377](http://ubuntuforums.org/showthread.php?t=2321328&page=2&p=13514377#post13514377)

Then again run:

```
sudo apt-get update
```

And post the output here. DO NOT apply any updates/upgrades yet! I suspect we'll have to make at least one more change but we need to do this one step at a time.

---

### Post by niceguy123 on 2016-07-07
Done.

```
@Dell:~$ sudo apt-get update
Get:1 http://deb.opera.com stable InRelease [2,592 B]
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://deb.opera.com stable InRelease                                      
Get:2 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://deb.opera.com stable/non-free amd64 Packages/DiffIndex              
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Get:3 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Ign http://www.openprinting.org lsb3.2 InRelease                               
Hit https://private-ppa.launchpad.net trusty Release                           
Get:4 http://us.archive.ubuntu.com trusty-backports InRelease [65.9 kB]        
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://www.openprinting.org lsb3.2 Release.gpg                             
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Get:5 http://us.archive.ubuntu.com trusty-security InRelease [65.9 kB]         
Get:6 http://us.archive.ubuntu.com trusty-proposed InRelease [65.9 kB]         
Hit http://www.openprinting.org lsb3.2 Release                                 
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                  
Get:7 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [790 kB] 
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                   
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en_AU                     
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Ign https://private-ppa.launchpad.net trusty/main Translation-en_AU            
Hit http://deb.opera.com stable/non-free i386 Packages                         
Get:9 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [363 kB]
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Ign http://deb.opera.com stable/non-free Translation-en_AU                     
Get:11 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [758 kB] 
Get:12 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Ign http://dl.google.com stable InRelease                                      
Get:13 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [365 kB]
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release                                 
Hit http://dl.google.com stable Release                                        
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Hit http://dl.google.com stable/main amd64 Packages                            
Get:15 http://us.archive.ubuntu.com trusty-updates/main Translation-en [396 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,227 B]
Get:17 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:18 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [191 kB]
Get:19 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [13.3 kB]
Get:20 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US               
Hit http://dl.google.com stable/main i386 Packages                             
Get:21 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [43.2 kB]
Get:22 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:23 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [13.3 kB]
Hit http://www.openprinting.org lsb3.2/contrib Translation-en                  
Get:24 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:25 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [43.2 kB]
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_AU               
Get:26 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:27 http://us.archive.ubuntu.com trusty-backports/main Translation-en [7,493 B]
Get:28 http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:29 http://us.archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
Get:30 http://us.archive.ubuntu.com trusty-backports/universe Translation-en [36.8 kB]
Get:31 http://us.archive.ubuntu.com trusty-security/main amd64 Packages [502 kB]
Get:32 http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:33 http://us.archive.ubuntu.com trusty-security/universe amd64 Packages [130 kB]
Get:34 http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages [4,989 B]
Get:35 http://us.archive.ubuntu.com trusty-security/main i386 Packages [469 kB]
Get:36 http://us.archive.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:37 http://us.archive.ubuntu.com trusty-security/universe i386 Packages [130 kB]
Get:38 http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages [5,170 B]
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Get:39 http://us.archive.ubuntu.com trusty-proposed/multiverse amd64 Packages [28 B]
Get:40 http://us.archive.ubuntu.com trusty-proposed/main amd64 Packages [146 kB]
Get:41 http://us.archive.ubuntu.com trusty-proposed/universe amd64 Packages [21.3 kB]
Get:42 http://us.archive.ubuntu.com trusty-proposed/restricted amd64 Packages [28 B]
Get:43 http://us.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:44 http://us.archive.ubuntu.com trusty-proposed/main i386 Packages [140 kB]
Get:45 http://us.archive.ubuntu.com trusty-proposed/universe i386 Packages [21.8 kB]
Get:46 http://us.archive.ubuntu.com trusty-proposed/restricted i386 Packages [28 B]
Get:47 http://us.archive.ubuntu.com trusty-proposed/main Translation-en [59.0 kB]
Get:48 http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en [28 B]
Get:49 http://us.archive.ubuntu.com trusty-proposed/restricted Translation-en [28 B]
Get:50 http://us.archive.ubuntu.com trusty-proposed/universe Translation-en [20.3 kB]
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_AU                         
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Ign http://dl.google.com stable/main Translation-en_AU                         
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/main Translation-en_AU                 
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en_AU           
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en_AU           
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Hit http://us.archive.ubuntu.com trusty/universe Translation-en_AU             
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 5,038 kB in 20s (247 kB/s)                                             
Reading package lists... Done
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
```

---

### Post by kansasnoob on 2016-07-07
We appear to be down to one error:

```
W: GPG error: http://deb.opera.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
```

So something is borked with the opera ppa???????

What seems odd is that I only see this PPA for Opera:

```
opera.list		     
opera.list.distUpgrade	     
```

Are you currently using Opera? I have Opera installed in Xenial and it shows up as:

```
opera-stable.list
```

I think the safest thing to do would be to look in Software & Updates under the Other Software tab and disable everything that refers to Opera. Then reinstall Opera from here:

[http://www.opera.com/download](http://www.opera.com/download)

**One more rather important thing.** While you're in Software & Updates look under the Updates tab and make sure to disable the proposed repos. Those updates have not been thoroughly tested yet.

So with the Opera PPA and the trusty-proposed repos disabled I'd try:

```
sudo apt-get update
```

If you see no errors I'd then try:

```
sudo apt-get dist-upgrade -s
```

The -s at the end means simulate so nothing will actually be changed but we could look at that output and have some idea how badly things are still messed up. If we're lucky the answer will be - not messed up at all.

---

### Post by niceguy123 on 2016-07-08
```
@Dell:~$ sudo apt-get update
Ign http://extras.ubuntu.com trusty InRelease
Ign http://dl.google.com stable InRelease                                      
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://dl.google.com stable InRelease                                      
Hit http://extras.ubuntu.com trusty Release                          
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://dl.google.com stable Release.gpg                          
Hit http://extras.ubuntu.com trusty/main Sources                     
Hit http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com trusty-security InRelease                     
Hit http://dl.google.com stable Release                                        
Ign http://www.openprinting.org lsb3.2 InRelease                               
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Hit http://www.openprinting.org lsb3.2 Release.gpg                             
Hit https://private-ppa.launchpad.net trusty Release                           
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://www.openprinting.org lsb3.2 Release                                 
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages         
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                   
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Ign http://extras.ubuntu.com trusty/main Translation-en_AU            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-security/main amd64 Packages           
Hit http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty-security/main i386 Packages   
Ign https://private-ppa.launchpad.net trusty/main Translation-en_AU 
Hit http://us.archive.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-security/universe i386 Packages        
Hit http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages            
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages     
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US               
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages   
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/main Translation-en_AU                 
Hit http://www.openprinting.org lsb3.2/contrib Translation-en                  
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_AU               
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en_AU           
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en_AU           
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Hit http://us.archive.ubuntu.com trusty/universe Translation-en_AU             
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_AU                         
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_AU                         
Reading package lists... Done 
```


```
@Dell:~$ sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  baloo evolution-common firefox-locale-ar firefox-locale-he kde-l10n-ar
  kde-l10n-engb kde-l10n-he libatk-bridge2.0-0:i386 libatk1.0-0:i386
  libatspi2.0-0:i386 libcairo-gobject2:i386 libcairo2:i386 libcolord1:i386
  libcurl3:i386 libdbus-glib-1-2:i386 libdbusmenu-glib4:i386
  libdbusmenu-gtk3-4:i386 libdbusmenu-gtk4:i386 liberror-perl libevolution
  libgconf-2-4:i386 libgdk-pixbuf2.0-0:i386 libgraphite2-3:i386
  libgtk-3-0:i386 libgtk2.0-0:i386 libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 libharfbuzz0b:i386 libhdb9-heimdal libidn11:i386
  libjasper1:i386 libkdc2-heimdal libkfilemetadata4 libmail-spf-perl libmpdec2
  libnetaddr-ip-perl libnspr4:i386 libnss3:i386 libntdb1 libpango-1.0-0:i386
  libpango1.0-0:i386 libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386
  libpangox-1.0-0:i386 libpangoxft-1.0-0:i386 libpixman-1-0:i386 libpst4
  librtmp0:i386 libsys-hostname-long-perl libwayland-client0:i386
  libwayland-cursor0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxft2:i386
  libxkbcommon0:i386 libxtst6:i386 libytnef0 linux-headers-3.13.0-24
  linux-headers-3.13.0-24-generic linux-headers-3.13.0-62
  linux-headers-3.13.0-62-generic linux-headers-3.13.0-83
  linux-headers-3.13.0-83-generic linux-image-3.13.0-24-generic
  linux-image-3.13.0-62-generic linux-image-3.13.0-83-generic
  linux-image-extra-3.13.0-24-generic linux-image-extra-3.13.0-62-generic
  linux-image-extra-3.13.0-83-generic pidgin-data python-ntdb re2c sa-compile
  spamassassin spamc
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  gir1.2-gtk-3.0 libgail-3-0 libgtk-3-0 libgtk-3-0:i386 libgtk-3-bin
  libgtk-3-common libmm-glib0 libnautilus-extension1a modemmanager nautilus
  nautilus-data oneconf oneconf-common python-oneconf python3-oneconf
15 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Inst libgtk-3-common [3.10.8-0ubuntu1.4] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [all])
Inst libgail-3-0 [3.10.8-0ubuntu1.4] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libgtk-3-0 [3.10.8-0ubuntu1.4] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64]) [libgtk-3-0:amd64 on libgtk-3-0:i386] [libgtk-3-0:i386 on libgtk-3-0:amd64] [libgtk-3-0:i386 ]
Inst libgtk-3-0:i386 [3.10.8-0ubuntu1.4] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386])
Inst libmm-glib0 [1.0.0-2ubuntu1] (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-gtk-3.0 [3.10.8-0ubuntu1.4] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Inst libgtk-3-bin [3.10.8-0ubuntu1.4] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Inst libnautilus-extension1a [1:3.10.1-0ubuntu9.9] (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [amd64])
Inst modemmanager [1.0.0-2ubuntu1] (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst nautilus-data [1:3.10.1-0ubuntu9.9] (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [all])
Inst nautilus [1:3.10.1-0ubuntu9.9] (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [amd64])
Inst oneconf-common [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst python3-oneconf [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst oneconf [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst python-oneconf [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf libgtk-3-common (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [all])
Conf libgtk-3-0 (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libgtk-3-0:i386 (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [i386])
Conf libgail-3-0 (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libmm-glib0 (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-gtk-3.0 (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libgtk-3-bin (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libnautilus-extension1a (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [amd64])
Conf modemmanager (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf nautilus-data (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [all])
Conf nautilus (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [amd64])
Conf oneconf-common (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf python3-oneconf (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf oneconf (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf python-oneconf (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
```

---

