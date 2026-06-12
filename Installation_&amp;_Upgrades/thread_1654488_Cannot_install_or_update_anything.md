---
title: "Cannot install or update anything"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by Senplanet on 2010-12-28
I got this error
"Requires installation of untrusted packages" 
when trying to install packages by Ubuntu Software center.

I found many solutions here in forums, but nothing seems to work for me.

1. I tried to change server to Main server, Best server, even some others... 
2. I checked the box in front of "unsupported updates"...
3. I tried update via sudo apt-get update but I got this result:
```

Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick Release.gpg
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick Release
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main i386 Packages
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted i386 Packages
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main i386 Packages
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted i386 Packages
Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:2 http://dl.google.com stable Release [1,347B]                             
Err http://dl.google.com stable Release                                        
  
Get:3 http://archive.ubuntu.com maverick Release.gpg [198B]                    
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en            
Get:4 http://extras.ubuntu.com maverick Release.gpg [65B]                     
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Get:5 http://archive.canonical.com maverick Release.gpg [198B]       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en  
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US     
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Get:6 http://archive.ubuntu.com maverick-updates Release.gpg [198B]  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US
Hit http://extras.ubuntu.com maverick Release                        
Get:7 http://archive.canonical.com maverick Release [5,925B]         
Err http://extras.ubuntu.com maverick Release                        
  
Ign http://archive.canonical.com maverick Release
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.canonical.com maverick/partner Sources/DiffIndex
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:8 http://archive.ubuntu.com maverick-backports Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Hit http://archive.canonical.com maverick/partner Sources
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Get:9 http://archive.ubuntu.com maverick-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://archive.canonical.com maverick/partner i386 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:10 http://archive.ubuntu.com maverick-proposed Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_US
Get:11 http://archive.ubuntu.com maverick Release [39.8kB]
Get:12 http://archive.ubuntu.com maverick-updates Release [31.4kB]
Get:13 http://archive.ubuntu.com maverick-backports Release [23.2kB]
Ign http://archive.ubuntu.com maverick Release             
Ign http://archive.ubuntu.com maverick-updates Release
Ign http://archive.ubuntu.com maverick-backports Release
Get:14 http://archive.ubuntu.com maverick-security Release [27.2kB]
Get:15 http://archive.ubuntu.com maverick-proposed Release [31.4kB]
Ign http://archive.ubuntu.com maverick-security Release     
Ign http://archive.ubuntu.com maverick-proposed Release
Ign http://archive.ubuntu.com maverick/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com maverick/main Sources/DiffIndex
Ign http://archive.ubuntu.com maverick/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com maverick/universe Sources/DiffIndex
Ign http://archive.ubuntu.com maverick/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/main Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/universe Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/main Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/universe Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-security/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-security/main Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-security/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-security/universe Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-security/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-security/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-security/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-security/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/main Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/universe Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/universe i386 Packages/DiffIndex
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/main Sources
Hit http://archive.ubuntu.com maverick/multiverse Sources
Hit http://archive.ubuntu.com maverick/universe Sources
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://archive.ubuntu.com maverick-updates/universe Sources                
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages              
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages        
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages          
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages        
Hit http://archive.ubuntu.com maverick-backports/main Sources                  
Hit http://archive.ubuntu.com maverick-backports/restricted Sources            
Hit http://archive.ubuntu.com maverick-backports/universe Sources              
Hit http://archive.ubuntu.com maverick-backports/multiverse Sources            
Hit http://archive.ubuntu.com maverick-backports/main i386 Packages            
Hit http://archive.ubuntu.com maverick-backports/restricted i386 Packages      
Hit http://archive.ubuntu.com maverick-backports/universe i386 Packages        
Hit http://archive.ubuntu.com maverick-backports/multiverse i386 Packages      
Hit http://archive.ubuntu.com maverick-security/restricted Sources             
Hit http://archive.ubuntu.com maverick-security/main Sources                   
Hit http://archive.ubuntu.com maverick-security/multiverse Sources             
Hit http://archive.ubuntu.com maverick-security/universe Sources               
Hit http://archive.ubuntu.com maverick-security/main i386 Packages             
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages       
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages         
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages       
Hit http://archive.ubuntu.com maverick-proposed/restricted Sources             
Hit http://archive.ubuntu.com maverick-proposed/main Sources                   
Hit http://archive.ubuntu.com maverick-proposed/multiverse Sources             
Hit http://archive.ubuntu.com maverick-proposed/universe Sources               
Hit http://archive.ubuntu.com maverick-proposed/restricted i386 Packages       
Hit http://archive.ubuntu.com maverick-proposed/main i386 Packages             
Hit http://archive.ubuntu.com maverick-proposed/multiverse i386 Packages       
Hit http://archive.ubuntu.com maverick-proposed/universe i386 Packages         
Fetched 2,803B in 8s (345B/s)                                                  
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com stable Release: Unknown error executing gpgv

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: Unknown error executing gpgv

W: GPG error: http://archive.canonical.com maverick Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com maverick Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com maverick-updates Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com maverick-backports Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com maverick-security Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com maverick-proposed Release: Unknown error executing gpgv
W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.


```

4. Updating via Update Manager gives the same error:
"Requires installation of untrusted packages"
5. I tried gpg –list-keys, result:
```
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC
```
6. Then I realized that there is not even one key file under
Ubuntu Software Center>> Authentication>>Trusted Software Providers

So I tried to click “Restore Defaults” but nothing happend
Well I dont know how this happened, neither how to fix it. 
Please , can you tell me any solution and reason to not reinstall ubuntu again.:(
Thank you

---

### Post by karthick87 on 2010-12-28
Try,
```
sudo apt-get autoclean
```
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Senplanet on 2010-12-28
I tried but it didn't solve the problem. However, something seems to be updated and the list of updates in Update Manager is obviously shorter than before, but when I try to install remaining packages or install via Software Center the error appear again.

---

### Post by lungten on 2010-12-28
The problem is with your APT sources list and the GPG keys associate with them. This problem can be solved in two ways.

1. Add the GPG keys for the sources for which you do not have the keys installed. You can get it from their site.
2. Remove those sources from your APT config (/etc/apt/sources.list or /etc/apt/sources.list.d/). 

You might want to remove/comment out the lines for CD-ROM since you'd get updated software from the Ubuntu repositories.

---

### Post by karthick87 on 2010-12-28
Try the following,
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
```
sudo apt-get install -f
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Senplanet on 2010-12-28
Thank you Karthick, but even after this I got the error :(

---

### Post by karthick87 on 2010-12-28
Can you post the following output once again,

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by Senplanet on 2010-12-28
for sudo apt-get update:
```
 
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick Release.gpg
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:2 http://dl.google.com stable Release [1,347B]                             
Err http://dl.google.com stable Release                                        
  
Get:3 http://archive.canonical.com maverick Release.gpg [198B]                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US
Get:4 http://extras.ubuntu.com maverick Release.gpg [65B]
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en           
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Get:5 http://archive.ubuntu.com maverick Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en            
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Get:6 http://archive.canonical.com maverick Release [5,925B]
Ign http://archive.canonical.com maverick Release                             
Hit http://extras.ubuntu.com maverick Release                          
Err http://extras.ubuntu.com maverick Release                        
  
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Get:7 http://archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.canonical.com maverick/partner Sources/DiffIndex
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:8 http://archive.ubuntu.com maverick-backports Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Hit http://archive.canonical.com maverick/partner Sources
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Get:9 http://archive.ubuntu.com maverick-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://archive.canonical.com maverick/partner i386 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:10 http://archive.ubuntu.com maverick-proposed Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_US
Get:11 http://archive.ubuntu.com maverick Release [39.8kB]
Get:12 http://archive.ubuntu.com maverick-updates Release [31.4kB]
Get:13 http://archive.ubuntu.com maverick-backports Release [23.2kB]
Get:14 http://archive.ubuntu.com maverick-security Release [27.2kB]
Ign http://archive.ubuntu.com maverick Release              
Ign http://archive.ubuntu.com maverick-updates Release
Ign http://archive.ubuntu.com maverick-backports Release
Ign http://archive.ubuntu.com maverick-security Release
Get:15 http://archive.ubuntu.com maverick-proposed Release [31.4kB]
Ign http://archive.ubuntu.com maverick-proposed Release
Ign http://archive.ubuntu.com maverick/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com maverick/main Sources/DiffIndex
Ign http://archive.ubuntu.com maverick/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com maverick/universe Sources/DiffIndex
Ign http://archive.ubuntu.com maverick/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/main Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/universe Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/main Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/universe Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-backports/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-security/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-security/main Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-security/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-security/universe Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-security/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-security/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-security/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-security/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/main Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/universe Sources/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-proposed/universe i386 Packages/DiffIndex
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/main Sources
Hit http://archive.ubuntu.com maverick/multiverse Sources
Hit http://archive.ubuntu.com maverick/universe Sources
Hit http://archive.ubuntu.com maverick/main i386 Packages                      
Hit http://archive.ubuntu.com maverick/restricted i386 Packages                
Hit http://archive.ubuntu.com maverick/universe i386 Packages                  
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages                
Hit http://archive.ubuntu.com maverick-updates/restricted Sources              
Hit http://archive.ubuntu.com maverick-updates/main Sources                    
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources              
Hit http://archive.ubuntu.com maverick-updates/universe Sources                
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages              
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages        
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages          
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages        
Hit http://archive.ubuntu.com maverick-backports/main Sources                  
Hit http://archive.ubuntu.com maverick-backports/restricted Sources            
Hit http://archive.ubuntu.com maverick-backports/universe Sources              
Hit http://archive.ubuntu.com maverick-backports/multiverse Sources            
Hit http://archive.ubuntu.com maverick-backports/main i386 Packages            
Hit http://archive.ubuntu.com maverick-backports/restricted i386 Packages      
Hit http://archive.ubuntu.com maverick-backports/universe i386 Packages        
Hit http://archive.ubuntu.com maverick-backports/multiverse i386 Packages      
Hit http://archive.ubuntu.com maverick-security/restricted Sources             
Hit http://archive.ubuntu.com maverick-security/main Sources                   
Hit http://archive.ubuntu.com maverick-security/multiverse Sources             
Hit http://archive.ubuntu.com maverick-security/universe Sources               
Hit http://archive.ubuntu.com maverick-security/main i386 Packages             
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages       
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages         
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages       
Hit http://archive.ubuntu.com maverick-proposed/restricted Sources             
Hit http://archive.ubuntu.com maverick-proposed/main Sources                   
Hit http://archive.ubuntu.com maverick-proposed/multiverse Sources             
Hit http://archive.ubuntu.com maverick-proposed/universe Sources               
Hit http://archive.ubuntu.com maverick-proposed/restricted i386 Packages       
Hit http://archive.ubuntu.com maverick-proposed/main i386 Packages             
Hit http://archive.ubuntu.com maverick-proposed/multiverse i386 Packages       
Hit http://archive.ubuntu.com maverick-proposed/universe i386 Packages         
Media change: please insert the disc labeled                                   
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter

Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick Release
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main i386 Packages
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted i386 Packages
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main i386 Packages
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted i386 Packages
Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Fetched 2,803B in 42s (66B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com stable Release: Unknown error executing gpgv

W: GPG error: http://archive.canonical.com maverick Release: Unknown error executing gpgv
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: Unknown error executing gpgv

W: GPG error: http://archive.ubuntu.com maverick Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com maverick-updates Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com maverick-backports Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com maverick-security Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com maverick-proposed Release: Unknown error executing gpgv
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Some index files failed to download, they have been ignored, or old ones used instead.


```

For sudo apt-get upgrade
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


```

---

### Post by Senplanet on 2010-12-30
> **lungten said:**
> The problem is with your APT sources list and the GPG keys associate with them. This problem can be solved in two ways.

1. Add the GPG keys for the sources for which you do not have the keys installed. You can get it from their site.
2. Remove those sources from your APT config (/etc/apt/sources.list or /etc/apt/sources.list.d/). 

You might want to remove/comment out the lines for CD-ROM since you'd get updated software from the Ubuntu repositories.

Do you mean, I need to add GPG key for source where GPG Error appeared? 
For example: 
```
W: GPG error: http://archive.canonical.com maverick Release: Unknown error executing gpgv
```
So I need do to add gpg key for [http://archive.canonical.com](http://archive.canonical.com) right?
But how to find gpg for each source? I mean , I tried to find on the side but nothing there seems like GPG... can you give me some example or Isn't an another way?

---

### Post by lungten on 2010-12-30
All repositories should have keys. Otherwise you can get rowdy software installed on your system.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Good example here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by adana01 on 2011-03-03
hi, i have same error. when i try to upgrade or update my reposities, i take this error. 

i go insane or help me anyone.

for example ;

when i type " sudo apt-get install konversation " it showns this.

i can not install anything.

----------------------------------------------------------------------------------------

aslan@aslan-ubuntu:~$ sudo apt-get install konversation
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  akonadi-server docbook-xsl docbook-xsl-doc-html hal hal-info icoutils kdebase-runtime kdebase-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdepim-runtime kdepimlibs-kio-plugins kdoctools
  konversation-data kubuntu-debug-installer libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadiprivate1 libattica0 libboost-program-options1.42.0 libclucene0ldbl libdbusmenu-qt2
  libdirectfb-1.2-9 libgif4 libhal-storage1 libhal1 libilmbase6 libindicate-qt0 libiodbc2 libkabc4 libkatepartinterfaces4 libkcal4 libkde3support4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4
  libkfile4 libkhtml5 libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4 libkmediaplayer4 libkmime4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpimutils4 libkpty4 libkresources4
  libkrosscore4 libkrossui4 libktexteditor4 libkutils4 libmailtransport4 libmicroblog4 libmodplug1 libmpcdec6 libmysqlclient16 libnepomuk4 libnepomukquery4a libopenexr6 libphonon4 libplasma3
  libpolkit-qt-1-0 libqapt-runtime libqapt1 libqca2 libqt4-dbus libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqtcore4
  libqtgui4 libqtwebkit4 libreadline5 libsolid4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libthreadweaver4 libts-0.0-0 libvirtodbc0 libxcb-shape0 libxcb-xv0 libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x mysql-client-core-5.1 mysql-common mysql-server-core-5.1 odbcinst odbcinst1debian2 oxygen-icon-theme phonon phonon-backend-xine plasma-scriptengine-javascript qapt-batch
  shared-desktop-ontologies smartdimmer soprano-daemon tsconf ttf-dejavu ttf-dejavu-extra virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
Suggested packages:
  libsaxon-java libxalan2-java docbook-xsl-saxon fop xalan dbtoepub gnome-device-manager libterm-readline-gnu-perl libterm-readline-perl-perl djvulibre-bin hspell libqca2-plugin-cyrus-sasl
  libqca2-plugin-gnupg libqca2-plugin-ossl libqca2-plugin-pkcs11 libqt4-dev qt4-qtconfig gxine xine-ui libxine1-doc libxine-doc libxine1-ffmpeg phonon-backend-gstreamer phonon-backend-vlc
  phonon-backend-mplayer
The following NEW packages will be installed:
  akonadi-server docbook-xsl docbook-xsl-doc-html hal hal-info icoutils kdebase-runtime kdebase-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdepim-runtime kdepimlibs-kio-plugins kdoctools
  konversation konversation-data kubuntu-debug-installer libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadiprivate1 libattica0 libboost-program-options1.42.0 libclucene0ldbl
  libdbusmenu-qt2 libdirectfb-1.2-9 libgif4 libhal-storage1 libhal1 libilmbase6 libindicate-qt0 libiodbc2 libkabc4 libkatepartinterfaces4 libkcal4 libkde3support4 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkfile4 libkhtml5 libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4 libkmediaplayer4 libkmime4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpimutils4 libkpty4
  libkresources4 libkrosscore4 libkrossui4 libktexteditor4 libkutils4 libmailtransport4 libmicroblog4 libmodplug1 libmpcdec6 libmysqlclient16 libnepomuk4 libnepomukquery4a libopenexr6 libphonon4 libplasma3
  libpolkit-qt-1-0 libqapt-runtime libqapt1 libqca2 libqt4-dbus libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqtcore4
  libqtgui4 libqtwebkit4 libreadline5 libsolid4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libthreadweaver4 libts-0.0-0 libvirtodbc0 libxcb-shape0 libxcb-xv0 libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x mysql-client-core-5.1 mysql-common mysql-server-core-5.1 odbcinst odbcinst1debian2 oxygen-icon-theme phonon phonon-backend-xine plasma-scriptengine-javascript qapt-batch
  shared-desktop-ontologies smartdimmer soprano-daemon tsconf ttf-dejavu ttf-dejavu-extra virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
0 upgraded, 124 newly installed, 0 to remove and 274 not upgraded.
Need to get 18.0MB/86.5MB of archives.
After this operation, 292MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kdelibs5-data libqtcore4 libqt4-xml libqt4-dbus libqt4-network libkdecore5 libkpty4 libkdesu5 libqtgui4 libqt4-svg libkdeui5 libkdnssd4 libnepomuk4 libsolid4 libkio5 libkfile4 libkjsapi4 libkparts4
  libktexteditor4 libkhtml5 libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkutils4 libnepomukquery4a libkdewebkit5 libqt4-opengl libqt4-script libthreadweaver4 libplasma3 kdebase-runtime-data
  libkatepartinterfaces4 libkjsembed4 libkntlm4 libkrosscore4 libkrossui4 kdoctools kdelibs-bin kdelibs5-plugins plasma-scriptengine-javascript kdebase-runtime libqt4-sql libqt4-designer libqt4-qt3support
  mysql-common libmysqlclient16 mysql-server-core-5.1 mysql-client-core-5.1 libqt4-sql-mysql kdepim-runtime libkde3support4
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libqtcore4 i386 4:4.7.0-0ubuntu4.2 [1,847kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libqt4-xml i386 4:4.7.0-0ubuntu4.2 [134kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libqt4-dbus i386 4:4.7.0-0ubuntu4.2 [238kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libqt4-network i386 4:4.7.0-0ubuntu4.2 [493kB]                                                                                                   
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libattica0 i386 0.1.4-1 [138kB]                                                                                                                          
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkdecore5 i386 4:4.5.1-0ubuntu8 [883kB]                                                                                                        
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkpty4 i386 4:4.5.1-0ubuntu8 [32.2kB]                                                                                                          
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkdesu5 i386 4:4.5.1-0ubuntu8 [48.4kB]                                                                                                         
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libqtgui4 i386 4:4.7.0-0ubuntu4.2 [4,108kB]                                                                                                      
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libdbusmenu-qt2 i386 0.6.4-0ubuntu1 [67.3kB]                                                                                                            
Get:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libqt4-svg i386 4:4.7.0-0ubuntu4.2 [180kB]                                                                                                      
Get:12 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkdeui5 i386 4:4.5.1-0ubuntu8 [1,182kB]                                                                                                       
Get:13 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkdnssd4 i386 4:4.5.1-0ubuntu8 [63.4kB]                                                                                                       
Get:14 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libclucene0ldbl i386 0.9.21b-2 [362kB]                                                                                                                  
Get:15 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libiodbc2 i386 3.52.6-4 [158kB]                                                                                                                         
Get:16 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main soprano-daemon i386 2.5.2+dfsg.1-0ubuntu1 [168kB]                                                                                                       
Get:17 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libsoprano4 i386 2.5.2+dfsg.1-0ubuntu1 [421kB]                                                                                                          
Get:18 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libnepomuk4 i386 4:4.5.1-0ubuntu8 [165kB]                                                                                                       
Get:19 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libsolid4 i386 4:4.5.1-0ubuntu8 [160kB]                                                                                                         
Get:20 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libstreams0 i386 0.7.2-1 [121kB]                                                                                                                        
Get:21 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libstreamanalyzer0 i386 0.7.2-1 [368kB]                                                                                                                 
Get:22 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkio5 i386 4:4.5.1-0ubuntu8 [767kB]                                                                                                           
Get:23 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkfile4 i386 4:4.5.1-0ubuntu8 [208kB]                                                                                                         
Get:24 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkjsapi4 i386 4:4.5.1-0ubuntu8 [216kB]                                                                                                        
Get:25 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkparts4 i386 4:4.5.1-0ubuntu8 [113kB]                                                                                                        
Get:26 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libktexteditor4 i386 4:4.5.1-0ubuntu8 [82.9kB]                                                                                                  
Get:27 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libphonon4 i386 4:4.7.0really4.4.2-0ubuntu1 [127kB]                                                                                                     
Get:28 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkhtml5 i386 4:4.5.1-0ubuntu8 [1,856kB]                                                                                                       
Get:29 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkmediaplayer4 i386 4:4.5.1-0ubuntu8 [28.8kB]                                                                                                 
Get:30 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libknewstuff3-4 i386 4:4.5.1-0ubuntu8 [157kB]
Get:31 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libknotifyconfig4 i386 4:4.5.1-0ubuntu8 [40.1kB]
Get:32 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libkutils4 i386 4:4.5.1-0ubuntu8 [128kB]
Get:33 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main libnepomukquery4a i386 4:4.5.1-0ubuntu8 [95.6kB]
Get:34 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libilmbase6 i386 1.0.1-3build2 [121kB]
Get:35 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libopenexr6 i386 1.6.1-4.1 [261kB]                                                                                                                      
Get:36 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libmodplug1 i386 1:0.8.8.1-1ubuntu1 [173kB]                                                                                                             
Get:37 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libmpcdec6 i386 2:0.1~r459-1 [34.3kB]                                                                                                                   
Get:38 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libxine1-bin i386 1.1.18.1-4ubuntu4 [1,360kB]                                                                                                           
Get:39 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libxine1-misc-plugins i386 1.1.18.1-4ubuntu4 [865kB]                                                                                                    
Get:40 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main tsconf all 1.0-7build1 [12.8kB]                                                                                                                         
Get:41 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libts-0.0-0 i386 1.0-7build1 [28.3kB]                                                                                                                   
Fetched 14.8MB in 1min 9s (212kB/s)                                                                                                                                                                            
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.7.0-0ubuntu4.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.7.0-0ubuntu4.2_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.7.0-0ubuntu4.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.7.0-0ubuntu4.2_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.7.0-0ubuntu4.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.7.0-0ubuntu4.2_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/attica/libattica0_0.1.4-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/attica/libattica0_0.1.4-1_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdecore5_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdecore5_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkpty4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkpty4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdesu5_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdesu5_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.7.0-0ubuntu4.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.7.0-0ubuntu4.2_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu-qt/libdbusmenu-qt2_0.6.4-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu-qt/libdbusmenu-qt2_0.6.4-0ubuntu1_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.7.0-0ubuntu4.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.7.0-0ubuntu4.2_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdeui5_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdeui5_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdnssd4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkdnssd4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/clucene-core/libclucene0ldbl_0.9.21b-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/clucene-core/libclucene0ldbl_0.9.21b-2_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libi/libiodbc2/libiodbc2_3.52.6-4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libi/libiodbc2/libiodbc2_3.52.6-4_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/soprano/soprano-daemon_2.5.2+dfsg.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/soprano/soprano-daemon_2.5.2+dfsg.1-0ubuntu1_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/soprano/libsoprano4_2.5.2+dfsg.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/soprano/libsoprano4_2.5.2+dfsg.1-0ubuntu1_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libnepomuk4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libnepomuk4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libsolid4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libsolid4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreams0_0.7.2-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreams0_0.7.2-1_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreamanalyzer0_0.7.2-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreamanalyzer0_0.7.2-1_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkio5_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkio5_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkfile4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkfile4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkjsapi4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkjsapi4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkparts4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkparts4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libktexteditor4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libktexteditor4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/phonon/libphonon4_4.7.0really4.4.2-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/phonon/libphonon4_4.7.0really4.4.2-0ubuntu1_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkhtml5_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkhtml5_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkmediaplayer4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkmediaplayer4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libknewstuff3-4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libknewstuff3-4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libknotifyconfig4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libknotifyconfig4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkutils4_4.5.1-0ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkutils4_4.5.1-0ubuntu8_i386.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

-------------------------------------------------------------------------------------------------------------------------

thanks

---

