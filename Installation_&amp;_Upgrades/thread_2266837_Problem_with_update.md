---
title: "Problem with update"
date: 2015-02-25
forum: Installation &amp; Upgrades
---

### Post by kevin134 on 2015-02-25
Ok so am a novice too linux unbuntu.
Still trying to get a grasp of things. 
So after going into terminal and doing sudo apt-get update
it comes up with the following which to me does not seem right.

```
kevin@kombat87:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty Release.gpg
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty Release
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_GB
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_GB
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Sources                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main amd64 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-en_GB                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-en                        
Ign [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic InRelease                              
Ign [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates InRelease                      
Ign [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports InRelease
Ign [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security InRelease
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic Release.gpg
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates Release.gpg
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports Release.gpg
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security Release.gpg
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic Release
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates Release                           
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports Release                         
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security Release                          
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/restricted Sources              
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/multiverse Sources
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/restricted amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/multiverse amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/restricted i386 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/multiverse i386 Packages       
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/multiverse Translation-en      
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/restricted Translation-en       
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/restricted Sources                        
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/main Sources
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/universe Sources                         
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/multiverse Sources                       
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/main amd64 Packages     
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/restricted amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/universe amd64 Packages                  
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/multiverse amd64 Packages                
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/main i386 Packages                       
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/restricted i386 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/universe i386 Packages 
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/multiverse i386 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/main Translation-en_GB 
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/main Translation-en    
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/multiverse Translation-en_GB
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/multiverse Translation-en
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/restricted Translation-en_GB
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/restricted Translation-en
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/universe Translation-en_GB
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic/universe Translation-en
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/restricted Sources
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/main Sources   
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/universe Sources
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/multiverse Sources
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/main amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/restricted amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/universe amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/multiverse amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/main i386 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/restricted i386 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/universe i386 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/multiverse i386 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/main Translation-en               
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/multiverse Translation-en         
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/restricted Translation-en
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-updates/universe Translation-en
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/main Sources 
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/universe Sources
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/main amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/universe amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/main i386 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/universe i386 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/main Translation-en            
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-backports/universe Translation-en         
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/restricted Sources               
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/main Sources    
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/universe Sources
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/multiverse Sources
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/main amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/restricted amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/universe amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/multiverse amd64 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/main i386 Packages
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/restricted i386 Packages         
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/universe i386 Packages           
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/multiverse i386 Packages         
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/main Translation-en
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/multiverse Translation-en
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/restricted Translation-en
Hit [http://mirror.vorboss.net](http://mirror.vorboss.net) utopic-security/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en
W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
```





If anyone could help me and let me know how to solve this problem that'd be brilliant as i want to make sure the system is up too date.
Plus i wanted to update blender but no luck with that either..:mad:

---

### Post by Impavidus on 2015-02-25
Under normal circumstances, the cdrom (live disk) should be disabled as software source. So find your software sources and untick the cdrom.

---

### Post by deadflowr on 2015-02-25
Open software and updates and uncheck the entries for the cdrom.
Or edit the sources.list file, in /etc/apt/sources.list
From a terminal, you would run
```
sudo nano /etc/apt/sources.list
```
in the top section should be entries for the cdrom
They will look something like this
```
deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
```
Add a # to the beginning of the line like so
```
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
```
Do so to each line which as the cdrom entry in it.

Then click ctrl + X to save and exit.
(Basically click Y(for yes) and hit enter.
Then re-run the update command.

Good Luck

---

### Post by kevin134 on 2015-02-25
Haha! I feel proper dumb now. Thanks for the help! Worked absoutely brilliantly :)

---

