---
title: "how can I solved this &quot;Err http://ppa.launchpad.net oneiric/main Sources            &quot;"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-12-28
I have tried to solve this problem wihtout succes.
----------------------------------------------------------
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages             
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US          
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Fetched 72 B in 1s (52 B/s)
W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by 2F4U on 2011-12-28
The repositories that receive errors are third party repositories, for example

[http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages)

and they don't have packages for oneiric (the path simply doesn't exist).

---

