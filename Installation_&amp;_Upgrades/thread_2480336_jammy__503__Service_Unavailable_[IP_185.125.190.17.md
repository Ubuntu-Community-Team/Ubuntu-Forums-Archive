---
title: "jammy  503  Service Unavailable [IP: 185.125.190.17 80]"
date: 2022-10-26
forum: Installation &amp; Upgrades
---

### Post by jg-jguk on 2022-10-26
Noticed this past week that ubuntu updates are struggling. I'm still on same wired Ethernet 500 mbps internet, so my connection all good.
Maybe ubuntu servers are overloaded?

Anyone know why it has these "ign" lines?

   apt-get updateHit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                       
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease                                                                                     
Hit:4 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                                                                
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security InRelease                               
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease                              
Hit:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jammy InRelease               
Ign:8 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy InRelease                           
Ign:9 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-updates InRelease
Ign:10 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-proposed InRelease
Ign:8 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy InRelease
Ign:9 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-updates InRelease
Ign:10 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-proposed InRelease
Ign:8 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy InRelease
Ign:9 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-updates InRelease
Ign:11 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-proposed Release
Ign:12 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy Release
Get:13 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-updates Release [40.5 kB]
Ign:11 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-proposed Release                                                                                                                  
Get:12 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy Release [40.4 kB]                                                                                                                 
Get:11 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-proposed Release [40.5 kB]
Fetched 121 kB in 1min 14s (1,638 B/s)
Reading package lists... Done


Sometimes it fails.


 Ign:117 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-proposed InRelease                                                       
Ign:118 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy Release                                                                  
Ign:59 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-updates InRelease
Ign:117 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-proposed InRelease
Ign:118 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy Release
Ign:59 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-updates InRelease
Ign:117 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-proposed InRelease
Ign:118 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy Release
Ign:59 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-updates InRelease
Err:117 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-proposed InRelease
  503  Service Unavailable [IP: 185.125.190.17 80]
Err:118 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy Release
  503  Service Unavailable [IP: 185.125.190.17 80]
Ign:119 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-updates Release
Ign:119 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-updates Release
Ign:119 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-updates Release
Err:119 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy-updates Release
  503  Service Unavailable [IP: 185.125.190.17 80]
Reading package lists... Done

---

### Post by tea for one on 2022-10-26
> **jg-jguk said:**
> 
Anyone know why it has these "ign" lines?   
```
Ign:8 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) jammy InRelease    
```                       

The ignore lines all begin with [COLOR="#FF0000"]ddebs[/COLOR], which is [s]not[/s] a debugging repository name.
Why not remove all the [COLOR="#FF0000"]ddebs[/COLOR] lines?

---

### Post by jg-jguk on 2022-10-26
I wonder where ddebs came from i that file. Surely I need to keep them? These must be the official repos

---

### Post by tea for one on 2022-10-26
I've never seen ddebs before so I conducted a little internet search and this appeared:-
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1982652](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1982652)
Any help?

These ddeb packages are part of a debugging process and probably not required for day-to-day use.
[https://wiki.ubuntu.com/Debug%20Symbol%20Packages](https://wiki.ubuntu.com/Debug%20Symbol%20Packages)

---

### Post by jg-jguk on 2022-10-26
Many thanks for your reply Tea for one. That's all clear.
That's it, now I understand, I had some core dumps and was trying to get a backtrace, so must have added them then. It's a shame they don't use a computer with a faster connection. I gave up in the end, as chromium wasn't built with debug symbols.

---

