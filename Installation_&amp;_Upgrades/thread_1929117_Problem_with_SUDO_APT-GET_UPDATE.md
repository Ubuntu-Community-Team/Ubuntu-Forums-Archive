---
title: "Problem with SUDO APT-GET UPDATE"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by dj shift on 2012-02-21
Please help, Have moved from 9.10 to 11.10 and I cannot install any software at all, have tried changing software source, tried using software center and nothing positive.
after sudo apt-get update, this is the error - please, I beg you help. want to instal GIMP, Audacity, and GNOME TWEAK all fail

sudo apt-get update
 [sudo] password for djshift: 
 Err [http://extras.ubuntu.com/](http://extras.ubuntu.com/) oneiric InRelease                                 
 
 Err [http://extras.ubuntu.com/](http://extras.ubuntu.com/) oneiric Release.gpg                               
   Unable to connect to extras.ubuntu.com:http:
 Err [http://archive.canonical.com/](http://archive.canonical.com/) oneiric InRelease                             
 
 Err [http://archive.canonical.com/](http://archive.canonical.com/) oneiric Release.gpg                           
   Unable to connect to archive.canonical.com:http: [IP: 91.189.88.33 80]
 Err [http://archive.ubuntu.com/](http://archive.ubuntu.com/) oneiric InRelease      
 
 Err [http://archive.ubuntu.com/](http://archive.ubuntu.com/) oneiric-updates InRelease
 
 Err [http://archive.ubuntu.com/](http://archive.ubuntu.com/) oneiric-backports InRelease
 
 Err [http://archive.ubuntu.com/](http://archive.ubuntu.com/) oneiric-security InRelease
 
 Err [http://archive.ubuntu.com/](http://archive.ubuntu.com/) oneiric-proposed InRelease
 
 Err [http://archive.ubuntu.com/](http://archive.ubuntu.com/) oneiric Release.gpg    
   Cannot initiate the connection to archive.ubuntu.com:80  (91.189.88.31). - connect (101: Network is unreachable) [IP:  91.189.88.31 80]
 Err [http://archive.ubuntu.com/](http://archive.ubuntu.com/) oneiric-updates Release.gpg
   Cannot initiate the connection to archive.ubuntu.com:80  (91.189.88.31). - connect (101: Network is unreachable) [IP:  91.189.88.31 80]
 Err [http://archive.ubuntu.com/](http://archive.ubuntu.com/) oneiric-backports Release.gpg
   Cannot initiate the connection to archive.ubuntu.com:80  (91.189.88.31). - connect (101: Network is unreachable) [IP:  91.189.88.31 80]
 Err [http://archive.ubuntu.com/](http://archive.ubuntu.com/) oneiric-security Release.gpg
   Cannot initiate the connection to archive.ubuntu.com:80  (91.189.88.31). - connect (101: Network is unreachable) [IP:  91.189.88.31 80]
 Err [http://archive.ubuntu.com/](http://archive.ubuntu.com/) oneiric-proposed Release.gpg
   Cannot initiate the connection to archive.ubuntu.com:80  (91.189.88.31). - connect (101: Network is unreachable) [IP:  91.189.88.31 80]
 Reading package lists... Done
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease)  
 
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease)  
 
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease)  
 
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)  
 
 W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/InRelease](http://archive.canonical.com/ubuntu/dists/oneiric/InRelease)  
 
 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease)  
 
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-proposed/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-proposed/InRelease)  
 
 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to extras.ubuntu.com:http:
 
 W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg](http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to archive.canonical.com:http: [IP: 91.189.88.33 80]
 
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)   Cannot initiate the connection to archive.ubuntu.com:80  (91.189.88.31). - connect (101: Network is unreachable) [IP:  91.189.88.31 80]
 
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)   Cannot initiate the connection to archive.ubuntu.com:80  (91.189.88.31). - connect (101: Network is unreachable) [IP:  91.189.88.31 80]
 
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg)   Cannot initiate the connection to archive.ubuntu.com:80  (91.189.88.31). - connect (101: Network is unreachable) [IP:  91.189.88.31 80]
 
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)   Cannot initiate the connection to archive.ubuntu.com:80  (91.189.88.31). - connect (101: Network is unreachable) [IP:  91.189.88.31 80]
 
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-proposed/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-proposed/Release.gpg)   Cannot initiate the connection to archive.ubuntu.com:80  (91.189.88.31). - connect (101: Network is unreachable) [IP:  91.189.88.31 80]
 
 W: Some index files failed to download. They have been ignored, or old ones used instead.
[[IMG]https://s-external.ak.fbcdn.net/safe_image.php?d=AQDEf7hwvAmtbct4&w=90&h=90&url=http%3A%2F%2Fextras.ubuntu.com%2Ficons%2Ffolder.gif[/IMG]]("http://extras.ubuntu.com/")**[Index of /]("http://extras.ubuntu.com/")** 
extras.ubuntu.com

---

### Post by roelforg on 2012-02-21
try pinging the servers,
i can access them just fine;
are you behind a proxy?
check your internet connection.
Check your firewall.

Anyone of them might prevent your pc from contacting the servers

---

### Post by dj shift on 2012-02-22
Yes iam behind a proxy

internet connection is fine

dont know how to check fire wall but iam operating frow a work LAN

---

### Post by roelforg on 2012-02-22
I'm gonna say:
the proxy did it!
The sigs are based on data that some proxy's change,
causing it to fail.

---

### Post by cortman on 2012-02-22
It's the proxy. Open System Settings (if you're using Unity, click the dash, and in the search box type "system settings", select the Network icon, and change the proxy settings accordingly under the Proxy tab.

---

### Post by Extirpator on 2012-02-29
I too have the same problem...also in Software center, I can't see the "Install" option..it only displays "Use this source" icon. Further in synaptic manager I can see only the installed softwares...and when I click on "Mark all upgrades", nothing happens. Please help me out. I guess there were a few hard shut downs but in disk utility self run tests, it says that number of bad sectors is None. So i think it is a problem related with proxy settings but how to resolve it? I have tried changing proxy settings in Network Settings but nothing works :confused:

---

