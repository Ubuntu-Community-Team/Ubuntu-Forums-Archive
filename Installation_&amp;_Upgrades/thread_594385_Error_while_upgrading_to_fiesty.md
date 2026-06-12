---
title: "Error while upgrading to fiesty"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Stoodle on 2007-10-27
While trying to update to fiesty, I got

> Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/edgy/dists/main/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/edgy/dists/main/main-all/binary-i386/Packages.gz) 404 Not Found
What to do....

---

### Post by zvacet on 2007-10-28
```
gksudo gedit /etc/apt/source.list
```

Put # sign in front of that line and any other unofficial repos.Save and close.

```
sudo aptitude update
```

Try to upgrade again.

---

### Post by Stoodle on 2007-10-28
Problem. What if when I try to look at that file, I don't see anything? Also, what is gksudo? whatis didn't help me much.

---

### Post by Seisen on 2007-10-28
When you open that file you will have a bunch of entries in the file otherwise you wouldn't be able to update at all.  Also gksudo is basically the sudo command for graphical applications.

---

### Post by zvacet on 2007-10-28
[http://ubuntuforums.org/showthread.php?t=593050]("http://ubuntuforums.org/showthread.php?t=593050")

---

### Post by Stoodle on 2007-10-29
The error it's giving me is strange though....I've seen what was inside that file before and i haven't touched it. The error it gives me says that there are update lists in the file because there is one it can't find. Yet, when I open it, I don't see anything.

 sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US     
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) main Release.gpg
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) main/main-all Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) main Release                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources            
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) main/main-all Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources        
[U][B] Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) main/main-all Packages         
  404 Not Found[/B][/U] <====This is my problem
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done

---

