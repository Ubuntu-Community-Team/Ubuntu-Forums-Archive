---
title: "can't download from karmic-updates"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dino99 on 2009-09-16
when i use apt-get update, all the repo are updated except from:

- karmic-updates
- karmic-backports

then

Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged'

E: Sub-process returned an error code

---

### Post by taavikko on 2009-09-16
Working fine here...
```
devil@core7:~$ upgrade
[sudo] password for devil: 
Get:1 http://archive.ubuntu.com karmic Release.gpg [189B]
Ign http://archive.ubuntu.com karmic/main Translation-en_US
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic/universe Translation-en_US  
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://archive.ubuntu.com karmic-updates Release.gpg         
Ign http://archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic-updates/universe Translation-en_US  
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com karmic-security Release.gpg                
Ign http://archive.ubuntu.com karmic-security/main Translation-en_US     
Ign http://archive.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic-security/universe Translation-en_US  
Ign http://archive.ubuntu.com karmic-security/multiverse Translation-en_US
Get:2 http://archive.ubuntu.com karmic Release [65.9kB]                   
Hit http://archive.ubuntu.com karmic-updates Release                      
Hit http://archive.ubuntu.com karmic-security Release                     
Get:3 http://archive.ubuntu.com karmic/main Packages [1347kB]             
Get:4 http://archive.ubuntu.com karmic/restricted Packages [7331B]        
Get:5 http://archive.ubuntu.com karmic/main Sources [634kB]               
Get:6 http://archive.ubuntu.com karmic/restricted Sources [2870B]
Get:7 http://archive.ubuntu.com karmic/universe Packages [5102kB]
Get:8 http://archive.ubuntu.com karmic/universe Sources [2767kB]
Get:9 http://archive.ubuntu.com karmic/multiverse Packages [191kB]
Get:10 http://archive.ubuntu.com karmic/multiverse Sources [117kB]
Hit http://archive.ubuntu.com karmic-updates/main Packages
Hit http://archive.ubuntu.com karmic-updates/restricted Packages
Hit http://archive.ubuntu.com karmic-updates/main Sources
Hit http://archive.ubuntu.com karmic-updates/restricted Sources
Hit http://archive.ubuntu.com karmic-updates/universe Packages
Hit http://archive.ubuntu.com karmic-updates/universe Sources
Hit http://archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://archive.ubuntu.com karmic-security/main Packages
Hit http://archive.ubuntu.com karmic-security/restricted Packages
Hit http://archive.ubuntu.com karmic-security/main Sources
Hit http://archive.ubuntu.com karmic-security/restricted Sources
Hit http://archive.ubuntu.com karmic-security/universe Packages
Hit http://archive.ubuntu.com karmic-security/universe Sources
Hit http://archive.ubuntu.com karmic-security/multiverse Packages
Hit http://archive.ubuntu.com karmic-security/multiverse Sources
Fetched 10.2MB in 12s (842kB/s)
Reading package lists... Done

```

updates- and backports- are used only in official releases. They're not in use in alphas.

---

### Post by Longinus00 on 2009-09-16
> **dino99 said:**
> when i use apt-get update, all the repo are updated except from:

- karmic-updates
- karmic-backports

then

Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged'

E: Sub-process returned an error code

Use aptitude, it doesn't rely on dbus.

---

### Post by dino99 on 2009-09-16
have had some doubts

work fine with aptitude

---

