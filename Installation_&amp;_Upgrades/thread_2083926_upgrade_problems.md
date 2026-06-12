---
title: "upgrade problems"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by kishkira on 2012-11-14
I recently upgraded to Ubutu 12.04. In doing so my wireless card is no longer recognized. when i follow the steps to trouble shoot i get several error messages all centered around Cyberlink Powerdvd and my computers inability to unistall it. I have tried to do so manually but it always incurs and error. any help in this matter would be appreciated

---

### Post by carl4926 on 2012-11-14
Is this a wubi install?
Because I'm pretty sure I never heard of this: Cyberlink Powerdvd
Except in winders

---

### Post by kishkira on 2012-11-14
The software center says " Cyberlink Power DVD is an integrated multimedia player that brings you the enjoyment of dvd movies".

---

### Post by kishkira on 2012-11-14
But as long as its on i cant complete my updates and it will not allow me to download any new software.

---

### Post by carl4926 on 2012-11-14
what do you get with

```
sudo apt-get update
```

---

### Post by Polydorus on 2012-11-14
Cyberlink Power DVD is what I had on XP.  A quick Google doesn't show a Linux version but it does show a few open source programs like:

CyberLink PowerDVD 9

[http://www.osalt.com/powerdvd](http://www.osalt.com/powerdvd)

---

### Post by kishkira on 2012-11-14
Err [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
  
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg
  Could not resolve 'archive.canonical.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/InRelease](http://archive.canonical.com/ubuntu/dists/precise/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.




thats what i get

---

### Post by varunendra on 2012-11-15
kishkira,

Is your objective wifi troubleshooting or upgrading/updating ?

If it is the wifi that you want to fix, please request a mod to change the title of your thread to something relevant, and move it to "Networking & Wireless" forum.

While doing apt-get update, you need to be connected to internet. So.. are you connected via cable ? It would also help in fixing the wifi.

For wifi issue, please follow this post and post back the result as asked in it : [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

---

### Post by quentinl on 2012-11-15
software update manager
or
sudo apt-get update

---

