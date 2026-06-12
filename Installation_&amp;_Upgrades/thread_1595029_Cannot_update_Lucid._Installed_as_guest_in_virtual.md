---
title: "Cannot update Lucid. Installed as guest in virtualbox"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by heysoos on 2010-10-12
I recently installed Lucid 10.04 as a guest OS on my Virtualbox [running on a Win. 7 host OS]
 
I cannot get apt-get update to work, it fails to find the server. I also see Failed to fetch messages when I invoke from the Update Manager. 
 
Interestingly, I can type in the IP into FF browser, and list all the files there. 
 
I believe this has something to do with the virtualbox, but can't determine why FF finds the servers just fine, but the update manager cannot.
 
When I invoke an apt-get update: 
 
$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg 
Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US 
Unable to connect to archive.canonical.com:http:
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources 
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources 
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages 
Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources 
Unable to connect to archive.canonical.com:http:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg 
Could not connect to us.archive.ubuntu.com:80 (91.189.92.172). - connect (110: Connection timed out) [IP: 91.189.92.172 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.172 80]
(truncated)
 
Please let me know if you can offer any recommendations.

---

