---
title: "Update Manager broken while updating to 7.10"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by novus721 on 2007-10-20
Hello all - 

So I updated this morning and it downloaded everything perfectly fine, but when it reached about ~15% installed/46 minutes left it hung indefinitely - it opened another window which stayed blank and frozen, and after letting it sit an hour it did nothing.

I restarted, and went into terminal entering
```
sudo apt-get install -f
```

which asked me to do
```
dpkg --configure -a
```

which seemed to have repaired everything as there are no more errors

However, after rebooting my Update Manager says 707 more updates need to be installed, yet when I got to open it the screen stays blank and I cannot terminate the program. 

Also, my GAIM crashes immediately upon attempted start, don't know how this is related except that partial updates are not good. I cannot afford to give this a clean update, any ideas? Thank you all!

---

### Post by Pumalite on 2007-10-20
Post the output of:
sudo apt-get update

---

### Post by novus721 on 2007-10-20
```
root@ubuntu-desk:~# sudo apt-get update
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:2 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Get:3 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]   
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_US           
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release                
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_US     
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_US       
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
Hit http://archive.canonical.com gutsy Release                      
Get:4 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]    
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Get:5 http://archive.ubuntu.com gutsy-security Release.gpg [191B]              
Ign http://archive.ubuntu.com gutsy-security/main Translation-en_US            
Ign http://archive.ubuntu.com gutsy-security/restricted Translation-en_US      
Ign http://archive.ubuntu.com gutsy-security/universe Translation-en_US        
Ign http://archive.ubuntu.com gutsy-security/multiverse Translation-en_US      
Get:6 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US                 
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Ign http://archive.canonical.com gutsy/partner Packages                        
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US     
Hit http://archive.ubuntu.com gutsy-backports Release                
Hit http://archive.ubuntu.com gutsy-updates Release                            
Hit http://archive.ubuntu.com gutsy-security Release                           
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://archive.ubuntu.com gutsy Release                                    
Hit http://archive.ubuntu.com gutsy-backports/main Packages                    
Hit http://archive.ubuntu.com gutsy-backports/restricted Packages              
Hit http://archive.ubuntu.com gutsy-backports/universe Packages                
Hit http://security.ubuntu.com gutsy-security/multiverse Sources               
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://archive.ubuntu.com gutsy-backports/main Sources
Hit http://archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://archive.ubuntu.com gutsy-backports/universe Sources
Hit http://archive.ubuntu.com gutsy-backports/multiverse Sources
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Sources
Hit http://archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://archive.ubuntu.com gutsy-security/main Packages
Hit http://archive.ubuntu.com gutsy-security/restricted Packages
Hit http://archive.ubuntu.com gutsy-security/universe Packages
Hit http://archive.ubuntu.com gutsy-security/multiverse Packages
Hit http://archive.ubuntu.com gutsy-security/main Sources
Hit http://archive.ubuntu.com gutsy-security/restricted Sources
Hit http://archive.ubuntu.com gutsy-security/universe Sources
Hit http://archive.ubuntu.com gutsy-security/multiverse Sources
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/universe Sources
Hit http://archive.ubuntu.com gutsy/multiverse Sources
Get:7 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Get:8 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release
Hit http://us.archive.ubuntu.com gutsy-updates Release
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Fetched 8B in 14s (1B/s)
Reading package lists... Done

```

---

### Post by Pumalite on 2007-10-20
Your apt-get seems to be working, but your system might need a reinstall.

---

### Post by novus721 on 2007-10-20
Any idea how to do this without a full fresh reinstall? Maybe downloading the CD and updating from that??? Thank you!

---

### Post by Pumalite on 2007-10-20
You could try it. It has to be the Alternate CD.

---

### Post by novus721 on 2007-10-20
SITUATION IS RESOLVED!

Thanks to another thread

[http://ubuntuforums.org/showthread.php?t=505033&highlight=reinstall+feisty](http://ubuntuforums.org/showthread.php?t=505033&highlight=reinstall+feisty)

I simply typed in 

```
sudo apt-get dist-upgrade
```

which continued on the install from where it left off, it took awhile, but everything is up and running now, thanks all

---

