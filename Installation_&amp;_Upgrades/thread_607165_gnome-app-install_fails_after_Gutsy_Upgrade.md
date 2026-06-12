---
title: "gnome-app-install fails after Gutsy Upgrade"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2007-11-08
After upgrading to Gutsy I get the following error when running gnome-app-install

/usr/bin/python: symbol lookup error: /usr/lib/python2.5/site-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_buffer_copy_flags_get_type 

Thanks,

Leo

---

### Post by bulldog on 2007-11-08
And the question would be?
Some extra info is welcome,like what are you planning to do.

---

### Post by Pumalite on 2007-11-08
Looks like a need for a clean install to me.

---

### Post by bulldog on 2007-11-08
> **Pumalite said:**
> Looks like a need for a clean install to me.
:lolflag:

---

### Post by Pumalite on 2007-11-08
> **bulldog said:**
> :lolflag:

:guitar:

---

### Post by lister171254 on 2007-11-08
Sorry, I thought it was clear what I wanted to do. I would like to add/remove applications via the appication menu bar.

Thanks,

Leo

---

### Post by Pumalite on 2007-11-08
Applications>Add/Remove

---

### Post by lister171254 on 2007-11-08
> **Pumalite said:**
> Applications>Add/Remove


That's what I'm trying to do. but when I select this nothing happens. That's why I ran the command from a terminal.

Thanks,

Leo

---

### Post by Pumalite on 2007-11-09
Post the output of:

sudo apt-get update

---

### Post by lister171254 on 2007-11-09
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg [191B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Translation-en_AU          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Translation-en_AU    
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports Release.gpg [191B]          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/main Translation-en_AU        
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/restricted Translation-en_AU  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/universe Translation-en_AU    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_AU  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release                     
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports Release [37.0kB]        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Sources            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Packages         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Packages   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Sources          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Sources    
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/main Packages [3054B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_AU 
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/restricted Packages [14B]
Get:8 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/universe Packages [1718B]
Get:9 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/multiverse Packages [14B]   
Get:10 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/main Sources [1470B]       
Get:11 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/restricted Sources [14B]   
Get:12 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/universe Sources [1639B]   
Get:13 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/multiverse Sources [14B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_AU                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_AU     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Fetched 45.2kB in 1s (23.0kB/s)

---

### Post by Pumalite on 2007-11-09
You have a sources.list, but not all get 'hit'. Maybe some servers are down. You could change your source to 'Main' temporarily.
System>Administration>Software Sources (change:'Download From')

---

### Post by lister171254 on 2007-11-09
Actually, it was set to the main server, I have now changes this to the Australian servers

Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Translation-en_AU
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Translation-en_AU
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_AU
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-security/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-security/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-security/universe Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-security Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-backports/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-security/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-security/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-security/universe Sources

---

