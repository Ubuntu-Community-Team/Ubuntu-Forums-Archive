---
title: "Utopic update fail (missing sources)"
date: 2015-10-14
forum: Installation &amp; Upgrades
---

### Post by Pablo W on 2015-10-14
Dear forum,

When trying to update (either through the update manager or through the terminal), ubuntu cannot find some sources. I have run ```
sudo apt-get update > ~/error.txt 

``` and the outcome is as follows (the first part of each sentence means "unable to fetch"):
```
W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/utopic-security/main/source/Sources  404  Not Found [IP: 91.189.91.24 80]

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/source/Sources  404  Not Found [IP: 91.189.91.24 80]

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/utopic-security/universe/source/Sources  404  Not Found [IP: 91.189.91.24 80]

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/utopic-security/multiverse/source/Sources  404  Not Found [IP: 91.189.91.24 80]

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/utopic-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.24 80]

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.24 80]

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.24 80]

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.24 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic/restricted/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic/universe/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-backports/main/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/source/Sources  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-backports/main/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-backports/restricted/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-backports/universe/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

W: Imposible obtener http://ar.archive.ubuntu.com/ubuntu/dists/utopic-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 200.236.31.4 80]

```

Any ideas about what is going on and how I can solve the issue? I am not an expert, please bear with my basic knowledge of Ubuntu.
Thanks!

---

### Post by howefield on 2015-10-14
Being end of life, 14.10 isn't likely to have updates for you.

[http://ubuntuforums.org/showthread.php?t=2288005](http://ubuntuforums.org/showthread.php?t=2288005)

I'd recommend getting to a supported release. If you are determined to stay on 14.10 you need to find out whether the repositories have been moved to old-releases yet, in which case that would be the cause of the above error. 

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by Pablo W on 2015-10-14
Thanks howefield.
I am not determined to stay on 14.10. I see that the suggested path forward would take me to another non-LTS version of Ubuntu, and then yet to another one. Is there a way to revert to 14.04 instead? Or maybe I should open a new thread on this? Thank you.

---

### Post by howefield on 2015-10-14
Only a clean install of 14.04.x would get you to the current LTS. 

However once there, you have the ability of to upgrade directly to the next LTS release which will be 16.04 or stay with 14.04 for the remainder of its life (till 2019).

Another option is installing 15.10 which is released next week and then to the next LTS 16.04 next April, obviously a more onerous path than LTS to LTS.

---

### Post by Pablo W on 2015-10-14
Thank you,  howefield.
I will back up my files and make a clean install of 14.04, then. In the long run, It seems the safest way to proceed.
Thank you for your advice.

---

