---
title: "Cannot Install Updates"
date: 2013-09-14
forum: Installation &amp; Upgrades
---

### Post by blake4 on 2013-09-14
Whenever I go to the Software Updater, it searches for updates and then says "*Failed to repository information.*" 

When I click "*Try Again*", I get the same. Then, I tried from terminal. Sudo apt-get update and got


```
Err http://ppa.launchpad.net raring/main amd64 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com raring-backports/universe i386 Packages
Err http://ppa.launchpad.net raring/main i386 Packages
  404  Not Found
Hit http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Hit http://us.archive.ubuntu.com raring-backports/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Hit http://us.archive.ubuntu.com raring-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-backports/universe Translation-en
Get:2 http://us.archive.ubuntu.com raring-proposed/restricted amd64 Packages [14 B]
Get:3 http://us.archive.ubuntu.com raring-proposed/multiverse amd64 Packages [14 B]
Get:4 http://us.archive.ubuntu.com raring-proposed/main amd64 Packages [56.3 kB]
Get:5 http://us.archive.ubuntu.com raring-proposed/universe amd64 Packages [35.4 kB]
Get:6 http://us.archive.ubuntu.com raring-proposed/restricted i386 Packages [14 B]
Get:7 http://us.archive.ubuntu.com raring-proposed/multiverse i386 Packages [14 B]
Get:8 http://us.archive.ubuntu.com raring-proposed/main i386 Packages [54.5 kB]
Get:9 http://us.archive.ubuntu.com raring-proposed/universe i386 Packages [35.8 kB]
Hit http://us.archive.ubuntu.com raring-proposed/main Translation-en           
Hit http://us.archive.ubuntu.com raring-proposed/multiverse Translation-en     
Hit http://us.archive.ubuntu.com raring-proposed/restricted Translation-en     
Hit http://us.archive.ubuntu.com raring-proposed/universe Translation-en       
Ign http://us.archive.ubuntu.com raring/main Translation-en_US                 
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US             
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US       
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US   
Ign http://us.archive.ubuntu.com raring-proposed/main Translation-en_US        
Ign http://us.archive.ubuntu.com raring-proposed/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com raring-proposed/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com raring-proposed/universe Translation-en_US    
Fetched 183 kB in 2min 41s (1,127 B/s)                                         
W: GPG error: http://www.duinsoft.nl debs Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E18CE6625CB26B26
W: Failed to fetch http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by bapoumba on 2013-09-14
Please deselect your ppas and try again.

---

### Post by blake4 on 2013-09-14
> **bapoumba said:**
> Please deselect your ppas and try again.

How do I do that?

---

### Post by bapoumba on 2013-09-14
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
You can deselect them from the software sources.

How did you install them ?

---

### Post by blake4 on 2013-09-14
I just installed them through the software center, (installed Screenlets, but these errors I'm not sure what they are referring to.)

---

### Post by bapoumba on 2013-09-14
The launchpad ppa and [http://www.duinsoft.nl/](http://www.duinsoft.nl/) are not found. I do not know what the second is :)
You need to untick them from the software sources.

---

### Post by ericrichards420 on 2013-09-14
try this Blake4 
Press and hold > Ctrl and Alt with your left hand and with your right hand press > t 
type this into your terminal.
```
[FONT=Ubuntu Mono]sudo apt-get -f install
```
now enter your password and press enter.[/FONT]

---

