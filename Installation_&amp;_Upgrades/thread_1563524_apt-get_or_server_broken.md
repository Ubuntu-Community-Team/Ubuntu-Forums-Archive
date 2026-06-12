---
title: "apt-get or server broken?"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by mrflashpants on 2010-08-29
I just attempted to update from karmic to lucid and the upgrade bombed out. now I get the following error from both of my ubuntu pc's when I run # sudo apt-get update

Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (202.158.214.106). - connect (111: Connection refused)
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU          
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU    
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU      
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU    
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release.gpg                     
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU  
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:
Err [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
  Unable to connect to au.archive.ubuntu.com:http:


Is this a problem with my network or the AU archive server?

Thanks!

---

### Post by zvacet on 2010-08-29
I checked links and they work for me.But you can switch to main server from system>admin>software sources and see if that helps.

---

### Post by mrflashpants on 2010-08-30
groovy, that worked!
:popcorn:

---

