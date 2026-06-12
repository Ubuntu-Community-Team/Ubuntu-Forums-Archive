---
title: "Canonical servers messed up? (Unable to download update packages)"
date: 2009-12-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Reiger on 2009-12-04
Trying to run an update:

> 
sudo aptitude safe-upgrade
Reading package lists... Done                  
Building dependency tree                       
Reading state information... Done              
Reading extended state information             
Initializing package states... Done            
Writing extended state information... Done     
Resolving dependencies...                      
Resolving dependencies...                      
The following NEW packages will be installed:  
  libgjs0{a}                                   
The following packages will be upgraded:       
  apparmor apparmor-utils gdm gjs gnome-icon-theme gstreamer0.10-tools libapparmor-perl libapparmor1 libdmx1 libgnome-menu2 libgnome2-0 libgnome2-common libgstreamer0.10-0 
  libx11-6 libx11-data libx11-dev libxext-dev libxext6 libxft-dev libxft2 libxi6 libxinerama1 libxss1 libxtst6 libxvmc1 libxxf86dga1 libxxf86vm1 lsb-base lsb-release       
  python-central tcpdump xfce4-power-manager xfce4-power-manager-data                                                                                                       
33 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.                                                                                                    
Need to get 11.7MB of archives. After unpacking 1,130kB will be used.                                                                                                       
Do you want to continue? [Y/n/?] y                                                                                                                                          
Writing extended state information... Done                                                                                                                                  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libx11-data 2:1.3.2-1ubuntu1                                                                                                    
  404  Not Found                                                                                                                                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libx11-dev 2:1.3.2-1ubuntu1                                                                                                     
  404  Not Found                                                                                                                                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libx11-6 2:1.3.2-1ubuntu1                                                                                                       
  404  Not Found                                                                                                                                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main lsb-base 4.0-0ubuntu6                                                                                                           
  404  Not Found                                                                                                                                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main python-central 0.6.11ubuntu10                                                                                                   
  404  Not Found                                                                                                                                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main lsb-release 4.0-0ubuntu6                                                                                                        
  404  Not Found                                                                                                                                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main apparmor 2.3.1+1403-0ubuntu30                                                                                                   
  404  Not Found                                                                                                                                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libapparmor1 2.3.1+1403-0ubuntu30                                                                                               
  404  Not Found                                                                                                                                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libapparmor-perl 2.3.1+1403-0ubuntu30                                                                                           
  404  Not Found                                                                                                                                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main apparmor-utils 2.3.1+1403-0ubuntu30                                                                                             
  404  Not Found                                                                                                                                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libxext-dev 2:1.1.1-1                                                                                                           
  404  Not Found                                                                                                                                                            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libxext6 2:1.1.1-1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main tcpdump 4.0.0-4ubuntu2
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libgnome2-common 2.28.0-1ubuntu2
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libgnome2-0 2.28.0-1ubuntu2
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main gdm 2.29.1-0ubuntu1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main gnome-icon-theme 2.28.0-1ubuntu1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libgstreamer0.10-0 0.10.25-3
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main gstreamer0.10-tools 0.10.25-3
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libdmx1 1:1.1.0-1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libgnome-menu2 2.28.0.1-0ubuntu3
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libxft-dev 2.1.14-1ubuntu1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libxft2 2.1.14-1ubuntu1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libxi6 2:1.3-1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libxinerama1 2:1.1-1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libxss1 1:1.2.0-1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libxtst6 2:1.1.0-1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libxvmc1 2:1.0.5-1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libxxf86dga1 2:1.1.1-1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main libxxf86vm1 1:1.1.0-1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe xfce4-power-manager 0.8.4.2-1ubuntu1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe xfce4-power-manager-data 0.8.4.2-1ubuntu1
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe gjs 0.4-3ubuntu2
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe libgjs0 0.4-3ubuntu2
  404  Not Found
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-data_1.3.2-1ubuntu1_all.deb:](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-data_1.3.2-1ubuntu1_all.deb:) 404  Not Found
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done


---

### Post by Gina on 2009-12-04
Have you tried the Main Server?  That's what I use for the testing phase - need to be up-to-date.  Although ATM, using Synaptic, it wants to remove several packages including gedit (no real problem) and ubuntu-desktop (needed surely!) plus some libraries.  So I'm waiting (and waiting) for a full update.

---

### Post by ronacc on 2009-12-04
repos loaded ok for me after I saw your post , try again , it wanted to remove a bunch of stuff and only install 2 so I'm waiting awhile.

---

### Post by buzzmandt on 2009-12-04
I got this too, I use kubuntu and it wanted to remove ubuntu desktop so I thought ok, then it got the 404 not founds so I stopped it.  I wait a bit and try again

---

### Post by Maheriano on 2009-12-04
You can change the servers you get this stuff from. I get mine from cpsc.ucalgary.ca, just up the street.

---

### Post by zika on 2009-12-04
> **Gina said:**
> Have you tried the Main Server?  That's what I use for the testing phase - need to be up-to-date.  Although ATM, using Synaptic, it wants to remove several packages including gedit (no real problem) and ubuntu-desktop (needed surely!) plus some libraries.  So I'm waiting (and waiting) for a full update.I'm on Main server and still [I get...]("http://ubuntuforums.org/showpost.php?p=8426996&postcount=18")
I've changed to USA server and some of problems are resolved. It seems it is more up-to-date ... at this moment, that is not my usual experience ...

---

### Post by andrek on 2009-12-04
I'm having the same on main servers, however the problem fixes itself after few retries.

---

### Post by Reiger on 2009-12-04
Yup. It's working again; problem solved (for now at least).

---

### Post by buzzmandt on 2009-12-04
working here too now

---

### Post by Gina on 2009-12-05
Working but still Partial Update - lots of packages held back.

---

