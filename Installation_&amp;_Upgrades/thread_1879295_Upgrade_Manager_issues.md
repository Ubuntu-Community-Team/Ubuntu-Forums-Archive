---
title: "Upgrade Manager issues"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by TheRacerX on 2011-11-11
ok heres my problem i just 7 proposed updates to my Linux Kernel Header stuff and it keeps telling me that i have a failed internet connection yet i still have internet, can someone help me ill provide screenshots of whatever you need im just confused about why its doing that, im running Ubuntu 10.10

---

### Post by raja.genupula on 2011-11-11
give me output of 

```
sudo apt-get update
```

thank you.

---

### Post by TheRacerX on 2011-11-11
i tried that but it didnt should the errors i didnt get any errors until i tried to install the updates the Update Manager showed me 
heres what i got 

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-2.6.35-31-generic_2.6.35-31.62_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-image-2.6.35-31-generic_2.6.35-31.62_i386.deb) 404  Not Found [IP: 91.189.92.176 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-2.6.35-31_2.6.35-31.62_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-2.6.35-31_2.6.35-31.62_all.deb) 404  Not Found [IP: 91.189.92.176 80]
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-2.6.35-31-generic_2.6.35-31.62_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/l/linux/linux-headers-2.6.35-31-generic_2.6.35-31.62_i386.deb) 404  Not Found [IP: 91.189.92.176 80]

---

### Post by TedinOz on 2011-11-11
I had this problem recently and was provided with a solution by subehsharma on this thread..[http://ubuntuforums.org/showthread.php?t=1878046](http://ubuntuforums.org/showthread.php?t=1878046)
Hope this works for you.

---

### Post by TheRacerX on 2011-11-11
that thread doesnt help me since im running 10.10 and the errors are coming from security update repositories not third party ones, and it wont even let me install fix404

---

### Post by raja.genupula on 2011-11-11
1...update manager -> settings -> change your server to other mirror and then update again

---

### Post by TheRacerX on 2011-11-11
tried that already, just made things worse

---

### Post by TheRacerX on 2011-11-12
now things have gotten way worse, it isnt letting me search, check or do any updating no matter what server i use, i KNOW its not my internet connection cause i can still surf the internet and download torrents at high speed, i dont know if maybe the Ubuntu servers are all having issues or what but im starting to get extremely annoyed with this entire situation.

---

### Post by raja.genupula on 2011-11-12
> **TheRacerX said:**
> now things have gotten way worse, it isnt letting me search, check or do any updating no matter what server i use, i KNOW its not my internet connection cause i can still surf the internet and download torrents at high speed, i dont know if maybe the Ubuntu servers are all having issues or what but im starting to get extremely annoyed with this entire situation.

hi man so this 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

are you sure that you're in main server ?

---

### Post by TheRacerX on 2011-11-12
i ran a test for the best server and it picked the Canadian Server since i live in Canada but even doesnt work correctly and i was on the main server until i ran the test

---

### Post by TheRacerX on 2011-11-12
this is what im getting right now 


theracerx@Cunningham:~$ sudo apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en_CA
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick Release.gpg [198B]                 
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Get:3 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_CA [10.1kB]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/amsn-daily/ppa/ubuntu/](http://ppa.launchpad.net/amsn-daily/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/amsn-daily/ppa/ubuntu/](http://ppa.launchpad.net/amsn-daily/ppa/ubuntu/) maverick/main Translation-en_CA
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/) maverick/main Translation-en_CA
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/chromium-daily/stable/ubuntu/](http://ppa.launchpad.net/chromium-daily/stable/ubuntu/) maverick/main Translation-en_CA
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_CA 
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Get:8 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_CA [425B]
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_CA   
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates Release.gpg [198B]         
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_CA
Ign [http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu/](http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu/](http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu/) maverick/main Translation-en_CA
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                    
Ign [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) maverick/main Translation-en_CA
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                    
Ign [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/) maverick/main Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_CA
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports Release.gpg [198B]      
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu/) maverick/main Translation-en_CA
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                    
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_CA
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en_CA
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                    
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_CA
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                    
Ign [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/](http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/) maverick/main Translation-en_CA
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security Release.gpg [198B]       
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en 
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_CA
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                    
Ign [http://ppa.launchpad.net/unixmen-com/pidgin/ubuntu/](http://ppa.launchpad.net/unixmen-com/pidgin/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/unixmen-com/pidgin/ubuntu/](http://ppa.launchpad.net/unixmen-com/pidgin/ubuntu/) maverick/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_CA
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-proposed Release.gpg [198B]       
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,752B]                      
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,746B]                      
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en 
Get:21 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_CA [10.1kB]
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,755B]                      
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,764B]                      
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,763B]                      
Get:25 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_CA [425B]
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_CA
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick Release [39.8kB]                  
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,732B]                      
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,761B]                      
Get:29 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,775B]                      
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates Release [31.4kB]          
Get:31 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports Release [27.2kB]        
Get:32 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,750B]                      
Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,770B]                      
Get:34 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,742B]                      
Get:35 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security Release [31.4kB]         
Get:36 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [2,937B]           
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [1,780B]                 
Get:38 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [2,610B]           
Get:39 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [1,508B]                 
Get:40 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [3,454B]           
Get:41 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [1,511B]                 
Get:42 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [3,280B]           
Get:43 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-proposed Release [32.4kB]         
Get:44 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [584B]                   
Get:45 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [666B]             
Get:46 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [4,008B]                 
Get:47 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [22.7kB]           
Get:48 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/main Sources [829kB]              
Get:49 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [743B]                   
Get:50 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [1,293B]           
Get:51 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [24.9kB]                 
Get:52 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [28.3kB]           
Get:53 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [634B]                   
Get:54 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [591B]             
Get:55 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [2,539B]                 
Get:56 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [5,259B]           
Get:57 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [950B]                   
Get:58 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [3,034B]           
Get:59 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/restricted Sources [4,370B]       
Get:60 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/universe Sources [4,179kB]        
Get:61 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                     
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_CA           
Get:62 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [9,762B]                      
Get:63 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources [1,073B]                 
Get:64 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages [1,216B]           
Get:65 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/multiverse Sources [151kB]        
Get:66 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/main i386 Packages [1,492kB]      
Get:67 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/restricted i386 Packages [5,992B] 
Get:68 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/universe i386 Packages [5,791kB]  
Get:69 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick/multiverse i386 Packages [183kB]  
Get:70 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/main Sources [143kB]      
Get:71 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/restricted Sources [778B] 
Get:72 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/universe Sources [50.6kB] 
Get:73 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/multiverse Sources [2,504B]
Get:74 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/main i386 Packages [388kB]
Get:75 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/restricted i386 Packages [1,797B]
Get:76 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/universe i386 Packages [171kB]
Get:77 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-updates/multiverse i386 Packages [5,197B]
Get:78 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/main i386 Packages [13.6kB]
Get:79 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/restricted i386 Packages [14B]
Get:80 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/universe i386 Packages [15.4kB]
Get:81 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-backports/multiverse i386 Packages [14B]
Get:82 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/main Sources [52.4kB]    
Get:83 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/restricted Sources [14B] 
Get:84 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/universe Sources [23.0kB]
Get:85 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/multiverse Sources [1,764B]
Get:86 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/main i386 Packages [169kB]
Get:87 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:88 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/universe i386 Packages [87.8kB]
Get:89 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-security/multiverse i386 Packages [3,733B]
Get:90 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-proposed/restricted i386 Packages [14B]
Get:91 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-proposed/main i386 Packages [124kB]
Get:92 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [1,124B]
Get:93 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) maverick-proposed/universe i386 Packages [20.8kB]
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.88.33), connection timed out
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
  Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_CA
  Unable to connect to archive.canonical.com:http:
Fetched 14.3MB in 2min 13s (107kB/s)                    
Reading package lists... Done
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33), connection timed out

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_CA.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_CA.bz2)  Unable to connect to archive.canonical.com:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by raja.genupula on 2011-11-12
Hi man 
..open update manager -> settings -> other software and uncheck the canonical PPA and try again

---

### Post by TheRacerX on 2011-11-12
there it worked without giving me a million connection error alerts thanks

---

### Post by raja.genupula on 2011-11-12
> **TheRacerX said:**
> there it worked without giving me a million connection error alerts thanks

welcome man! :D:D:D:D

---

### Post by TheRacerX on 2011-11-12
why would it be doing that though arent the conical PPAs where i get my security updates for the OS?

---

### Post by raja.genupula on 2011-11-12
> **TheRacerX said:**
> why would it be doing that though arent the conical PPAs where i get my security updates for the OS?

at settings window it self i think thats one is 2nd tab , there i think security already get checked so you gonna receive all security updates

---

